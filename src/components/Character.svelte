<script>
    // Props
	export let toggleTheme;    
    export let isDarkTheme;

    // Imports
    import Heading from "./UI/molecules/Heading.svelte";
    import SearchBar from "./UI/molecules/SearchBar.svelte";
    import Loading from "./UI/molecules/Loading.svelte";
    import NotFound from "./UI/molecules/NotFound.svelte";
    import Avatar from "./UI/atoms/Avatar.svelte";
</script>

<section class='w-full max-w-4xl'>
    <Heading toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
    <SearchBar isDarkTheme={isDarkTheme} />

    <!-- <Loading /> -->
    <!-- <NotFound /> -->

    <article class='rounded mt-10 px-8 py-10 bg-green dark:bg-white text-white dark:text-green grid gap-y-10 sm:grid-cols-[max-content_1fr] gap-x-10'>
        <Avatar
            src='https://elcomercio.pe/resizer/BhawkKwlyELCQcktjrhY8lcF8ag=/1200x1200/smart/filters:format(jpeg):quality(75)/cloudfront-us-east-1.images.arcpublishing.com/elcomercio/JNUIYEQLQ5FH5C7U3WNGM7OHF4.jpg'
            alt='Rick Sanchez'
        />

        <div class='space-y-10'>
            <div>
                <h2 class='text-2xl font-semibold tracking-wide'>Rick Sanchez</h2>
                <span class='text-sm tracking-wide'>Earth (C-137)</span>
            </div>

            <ul class='grid gap-y-4 max-w-lg md:flex flex-wrap items-center justify-between'>
                <li class='space-y-3'>
                    <h3 class='tracking-wide font-semibold'>Status</h3>
                    <p class='text-sm tracking-wide'>Alive</p>
                </li>
                <li class='space-y-3'>
                    <h3 class='tracking-wide font-semibold'>Location</h3>
                    <p class='text-sm tracking-wide'>Citadel of Ricks</p>
                </li>
                <li class='space-y-3'>
                    <h3 class='tracking-wide font-semibold'>Species</h3>
                    <p class='text-sm tracking-wide'>Human</p>
                </li>
                <li class='space-y-3'>
                    <h3 class='tracking-wide font-semibold'>Type</h3>
                    <p class='text-sm tracking-wide'>Not available</p>
                </li>
            </ul>

            <ul class="space-y-3 max-w-lg">
                <li class='flex flex-wrap items-center justify-between space-x-1'>
                    <h3 class='tracking-wide font-semibold'>First appearance</h3>
                    <p class='text-sm tracking-wide'><span class='font-semibold'>“Pilot”</span> - December 2, 2013</p>
                </li>
                <li class='flex flex-wrap items-center justify-between space-x-1'>
                    <h3 class='tracking-wide font-semibold'>N.º  seasons</h3>
                    <p class='text-sm tracking-wide'>5</p>
                </li>
                <li class='flex flex-wrap items-center justify-between space-x-1'>
                    <h3 class='tracking-wide font-semibold'>N.º episodes</h3>
                    <p class='text-sm tracking-wide'>51</p>
                </li>
            </ul>
        </div>
    </article>
</section>