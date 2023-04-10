<script>
	export let toggleTheme;    
    export let isDarkTheme;

    import Heading from "./UI/molecules/Heading.svelte";
    import SearchBar from "./UI/molecules/SearchBar.svelte";
    import Loading from "./UI/molecules/Loading.svelte";
    import NotFound from "./UI/molecules/NotFound.svelte";
</script>

<section class='w-full max-w-4xl'>
    <Heading toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
    <SearchBar isDarkTheme={isDarkTheme} />

    <!-- <Loading /> -->
    <!-- <NotFound /> -->
</section>