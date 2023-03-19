<script>
    import MainBanner from "../../lib/MainBanner.svelte";
    import HouseBanner from "../../lib/HouseBanner.svelte";
    import Cup from "../../lib/Cup.svelte";

    let houses = [
        { name: 'morlais', color: 'green'},
        { name: 'trevithick', color: 'red'},
        { name: 'tydfil', color: 'blue'},
        { name: 'glyndwr', color: 'yellow'},
    ]

    houses.forEach(house => {
        console.log(house)
    });
</script>

<main>
    <div class="banner">
        <MainBanner title={"Caedraw Cup Banner"} />
    </div>
    <div class="cup">
        <Cup title={'Cup'} />
    </div>
    {#each houses as house}
        <div class={house.name}>
            <HouseBanner house={house.name} color={house.color} />
        </div>
    {/each}
    <div class="current">
        <MainBanner title={"Current"} />
    </div>
</main>

<style>
    main {
        display: grid;
        padding: 1rem;
        gap: .5rem;
        text-align: center;
        grid-template-columns: 1fr;
    }
    @media screen and (min-width: 600px) {
        main {
            height: 100vh;
            grid-template-columns: repeat(4, 1fr);
            grid-template-rows: auto 1fr 2fr auto;
            grid-template-areas: 
                "banner banner banner banner"
                "trevithick morlais tydfil glyndwr"
                "cup cup cup cup"
                "current current current current" 
            ;
        }
        .banner     { grid-area: banner; }
        .cup        { grid-area: cup; }
        .current    { grid-area: current; }
        .trevithick { grid-area: trevithick; }
        .morlais    { grid-area: morlais; }
        .tydfil     { grid-area: tydfil; }
        .glyndwr    { grid-area: glyndwr;}
    }
    @media screen and (min-width: 900px) {
        main {
            height: 100vh;
            grid-template-columns: 1fr 1fr 3fr 1fr 1fr;
            grid-template-rows: auto 1fr auto;
            grid-template-areas: 
                "banner banner banner banner banner"
                "trevithick morlais cup tydfil glyndwr"
                "current current current current current"
            ;
        }
    }
    div {
        border: 1px solid #fff;
        background-color: rgba(0, 0, 0, 0.4);
        padding: 1rem;
    }
</style>