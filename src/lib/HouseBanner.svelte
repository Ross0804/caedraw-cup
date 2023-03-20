<script>
    export let house
    import { housePoints } from "../stores";
</script>

<main>
    <h1 >{house}</h1>
    <p>{$housePoints[house]}</p>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
    }
    h1 {
        margin: 0;
        font-size: 1rem;
    }
</style>
