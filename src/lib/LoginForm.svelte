<script>
    import {goto} from '$app/navigation'

    let password = '1234'
    let userInput = ''
    let errorMsg = ''

    const loginTeacher = () => {
        if (!userInput) {
            errorMsg = 'Password cannot be blank'
            return
        }

        if (userInput === password) {
            setTimeout(() => goto('/teacher'), 0)
        } else {
            errorMsg = 'Incorrect Password'
        }
    }
</script>

<form>
    <h1>Caedraw Cup</h1>
    <input type="password" placeholder="Password" bind:value={userInput}>
    <div>
        <button on:click={loginTeacher}>Teacher</button>
        <button on:click={() => setTimeout(() => goto('/student'), 0)} class="guest">Student</button>
    </div>
    {#if errorMsg}
        <p>{errorMsg}</p>
    {/if}
</form>

<style>
    form {
        background-color: rgba(0, 0 , 0, 0.4);
        padding: 1rem;
        margin: 0;
        margin-top: -5rem;
        min-width: 400px;
        border-radius: 1rem;
    }
    form div {
        display: flex;
        gap: 1rem;
    }
    h1 {
        margin: 0;
        margin-bottom: 1rem;
        text-align: center;
        color: #d8d8d8;
    }
    p {
        margin: 0;
        text-align: center;
    }
    .guest {
        background-color: green;
        border: none;
    }
</style>