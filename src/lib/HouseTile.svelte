<script>
    export let data;
    let sliderValue = 1
</script>

<article>
    <header>
        <h3>{data.name} {data.points}</h3>
    </header>
    <div>
        <p>Add Points</p>
        <div class="options">
            <button class="btnGreen">1</button>
            <button class="btnGreen">5</button>
            <button class="btnGreen">10</button>
        </div>
        <p>Remove Points</p>
        <div class="options">
            <button class="btnRed">1</button>
            <button class="btnRed">5</button>
            <button class="btnRed">10</button>
        </div>
    </div>
</article>

<style>
    h3 {
        margin: 0;
        font-size: 1.2rem;
        text-align: center;
    }
    article {
        margin: 0;
    }
    .options {
        display: flex;
        gap: 1rem;
    }
    header {
        padding: 1rem;
    }
    button {
        background-color: rgba(0, 0, 0, 0);
    }
    button:hover {
        border: 1px solid #fff;
        color: #fff;
    }
    .btnGreen {
        border: 1px solid green;
        color: green;
    }
    .btnRed {
        border: 1px solid red;
        color: red;
    }
</style>
