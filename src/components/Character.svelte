<script>
	export let toggleTheme;    
    export let isDarkTheme;

    import Heading from "./UI/molecules/Heading.svelte";
</script>

<section class='w-full max-w-4xl'>
    <Heading toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
</section>