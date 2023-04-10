<script>
    export let toggleTheme;    
    export let isDarkTheme;

    import Logo from '../atoms/Logo.svelte';
    import ThemeBtn from '../atoms/ThemeBtn.svelte';
</script>

<div class='flex items-center justify-between space-x-2'>
    <Logo />
    <ThemeBtn toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
</div>