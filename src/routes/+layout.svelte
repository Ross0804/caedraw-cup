<script>
    import {createClient, setContextClient} from '@urql/svelte'
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
</script>

<svelte:head>
    <link rel="stylesheet" href="https://unpkg.com/@picocss/pico@1.*/css/pico.min.css">
</svelte:head>

<slot></slot>