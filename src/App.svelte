<script>
  import { onMount } from 'svelte';

  import "./app.css";
  import Character from "./components/Character.svelte";

  let isDarkTheme = false;

  /*----- Lifecycle -----*/
  onMount(() => {
    const themeLS = localStorage.getItem('theme');

    if (!themeLS) {
      localStorage.setItem('theme', JSON.stringify('dark'));
      isDarkTheme = true;
    }
    else {
      isDarkTheme = JSON.parse(themeLS) === 'dark' ? true : false;
    }
  });

  /*----- Utilities -----*/
  function toggleTheme(){
    isDarkTheme = !isDarkTheme;
    localStorage.setItem('theme', JSON.stringify(isDarkTheme ? 'dark' : 'light'));
  }
</script>

<div class:dark={isDarkTheme}>
  <main class='min-h-screen grid place-items-center bg-white dark:bg-green px-4'>
    <Character toggleTheme={toggleTheme} isDarkTheme={isDarkTheme} />
  </main>
</div>