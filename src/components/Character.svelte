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

    // State
    let searchedValue = '';
    let timer;

    // Debounced search value
    function debounced(value){
        // Clear prev timeout
        clearTimeout(timer);

        // Wait and save
        timer = setTimeout(() => {
            searchedValue = value;
        }, 750);
    };

    // Fetch rick and morty character
    async function fetchCharacterFirstAppearance(characterFirstEpisode){
        try{
            // Fetch first episode info
            const firstAppearance = await fetch(characterFirstEpisode);
            const { name, air_date } = await firstAppearance.json();
            return [name, air_date];
        }
        catch(error){
            console.log('fetchCharacterFirstAppearance', error);
        }
    }

    async function fetchCharacter(characterName){
        if(!characterName) return null;

        const URL = `https://rickandmortyapi.com/api/character/?name=${characterName}`;

        // Fetch character info
        const characterInfo = await fetch(URL);
        const data = await characterInfo.json();

        if (data.results) {
            // If character was found
            const firstAppearance = await fetchCharacterFirstAppearance(data.results[0].episode[0]);
            return { ...data.results[0], firstAppearance: firstAppearance }; 
        }
        else {
            throw new Error(data);
        }
    }

    // Use for awaiting block
    let promise = fetchCharacter();
 
    function handleKeyup(searchedValue) {
        promise = fetchCharacter(searchedValue);
    }

    // Fetch character when search value changes
    $: if(searchedValue) handleKeyup(searchedValue);
</script>

<section class='w-full max-w-4xl'>
    <Heading toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
    <SearchBar isDarkTheme={isDarkTheme} debounced={debounced} />

    {#await promise} 
        <Loading />
	{:then character}
        {#if character && searchedValue !== ''}
            <article class='rounded mt-10 px-8 py-10 bg-green dark:bg-white text-whitE dark:text-green grid gap-y-10 sm:grid-cols-[max-content_1fr] gap-x-10'>
                <Avatar
                    src={character.image}
                    alt={character.name}
                />

                <div class='space-y-10'>
                    <div>
                        <h2 class='text-2xl font-semibold tracking-wide'>{character.name}</h2>
                        <span class='text-sm tracking-wide'>{character.origin.name}</span>
                    </div>

                    <ul class='grid gap-y-4 max-w-lg md:flex flex-wrap items-center justify-between'>
                        <li class='space-y-3'>
                            <h3 class='tracking-wide font-semibold'>Status</h3>
                            <p class='text-sm tracking-wide'>{character.status}</p>
                        </li>
                        <li class='space-y-3'>
                            <h3 class='tracking-wide font-semibold'>Location</h3>
                            <p class='text-sm tracking-wide'>{character.location.name}</p>
                        </li>
                        <li class='space-y-3'>
                            <h3 class='tracking-wide font-semibold'>Species</h3>
                            <p class='text-sm tracking-wide'>{character.species}</p>
                        </li>
                        <li class='space-y-3'>
                            <h3 class='tracking-wide font-semibold'>Type</h3>
                            <p class='text-sm tracking-wide'>{character.type || 'Not available'}</p>
                        </li>
                    </ul>

                    <ul class="space-y-3 max-w-lg">
                        <li class='flex flex-wrap items-center justify-between space-x-1'>
                            <h3 class='tracking-wide font-semibold'>First appearance</h3>
                            <p class='text-sm tracking-wide'>
                                <span class='font-semibold'>”{character.firstAppearance[0]}”</span> - {character.firstAppearance[1]}
                            </p>
                        </li>
                        <li class='flex flex-wrap items-center justify-between space-x-1'>
                            <h3 class='tracking-wide font-semibold'>N.º episodes</h3>
                            <p class='text-sm tracking-wide'>{character.episode.length}</p>
                        </li>
                    </ul>
                </div>
            </article>
        {/if}
	{:catch error}
        {#if searchedValue !== ''}
            <NotFound />
         {/if}
    {/await}
</section>