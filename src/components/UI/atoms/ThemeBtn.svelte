<script>
    export let toggleTheme;
    export let isDarkTheme;    

    import Icon from 'svelte-icons-pack/Icon.svelte';
    import FaMoon from 'svelte-icons-pack/fa/FaMoon';
    import FaSun from 'svelte-icons-pack/fa/FaSun';
</script>

<button class='flex items-center justify-between' type='button' on:click={toggleTheme}>
    <span class='text-green dark:text-white uppercase tracking-wide mr-2 text-xl'>
        {#if isDarkTheme}
            light
        {:else}
            dark
        {/if}
    </span>

    {#if isDarkTheme}
        <Icon src={FaSun} color='#F5F5F5' />
    {:else}
        <Icon src={FaMoon} color='#068596' />
    {/if}
</button>