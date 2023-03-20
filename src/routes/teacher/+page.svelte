<script>
    import { queryStore, gql, getContextClient } from "@urql/svelte";
    import Header from "../../lib/Header.svelte";
    import HouseTile from "../../lib/HouseTile.svelte";

    const AllHouses = queryStore({
        client: getContextClient(),
        query: gql`
            query GetAllHouses {
                allHouses {
                    data {
                        name
                        points
                    }
                }
            }
        `,
    });
</script>

<Header />

<main>
    <div class="controlsArea">
        {#if $AllHouses.fetching}
            <p>Loading...</p>
        {:else if $AllHouses.error}
            <p>Oh no... {$AllHouses.error.message}</p>
        {:else}
            {#each $AllHouses.data.allHouses.data as house}
                <HouseTile data={house} />
            {/each}
        {/if}
    </div>
</main>

<style>
    main {
        margin: 1rem;
        display: grid;
        grid-template-columns: repeat(1, 1fr);
        gap: 1rem;
    }
    .controlsArea {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1rem;
    }
</style>