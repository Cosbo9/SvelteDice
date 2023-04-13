<script>
    import { goto } from '$app/navigation'

    const handleClick = () => {
        goto('/')
    }
</script>

<header><p on:click={handleClick}>Header</p></header>
<slot />
