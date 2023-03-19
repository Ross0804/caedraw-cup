<script>
    import {queryStore, gql, getContextClient} from '@urql/svelte'

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