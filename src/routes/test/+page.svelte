<script>
    import {createClient, setContextClient, queryStore, gql, getContextClient} from 'urql/svelte'

    const client = createClient({
        url: 'https://graphql.fauna.com/graphql',
        fetchOptions: () => {
            const token = import.meta.env.VITE_PUBLIC_FAUNA_KEY;
            return {
                headers: { authorization: token ? `Bearer ${token}` : '' },
            };
        }
    })

    setContextClient(client)

    const housePoints = queryStore({
        client: getContextClient(),
        query: gql `
        query HouseByID{
            findHouseByID(id: "359636213925151321") {
                name
                points
            }
        }
        `
    })
</script>

{#if $housePoints.fetching}
    <p>Loading...</p>
{:else if $housePoints.error}
    <p>Oh no... {$housePoints.error.message}</p>
{:else}
    <ul>
        <li>{$housePoints.data.findHouseByID.name}</li>
        <li>{$housePoints.data.findHouseByID.points}</li>
    </ul>
{/if}