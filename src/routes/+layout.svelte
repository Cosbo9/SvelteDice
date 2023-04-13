<script>
    import {goto} from '$app/navigation'

    const handleClick = () => {
        goto('/')
    }
</script>

<header><p on:click={handleClick}>Header</p></header>
<slot/>

<style>
    header {
        padding: 1rem;
        background-color: #494949;
    }

    p {
        font-size: 2em;
        font-weight: 600;
        color: #e7e6e6;
        cursor: pointer;
    }
</style>