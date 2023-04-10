<script>
    export let isDarkTheme;
    import Icon from 'svelte-icons-pack/Icon.svelte';
    import FaSearch from 'svelte-icons-pack/fa/FaSolidSearch';
</script>

<article class='mt-10 relative'>
    <label for="search" class='absolute invisible'>Search character...</label>

    {#if isDarkTheme}
        <Icon src={FaSearch} color='#068596' className='top-8 left-4 absolute' />
    {:else}
        <Icon src={FaSearch} color='#F5F5F5' className='top-8 left-4 absolute' />
    {/if}

    <input
        placeholder='Search character...'
        class='placeholder-white dark:placeholder-green rounded w-full
        h-20 px-12 block bg-green dark:bg-white text-white dark:text-green' 
        type="search"
        id="search"
    />
</article>