<script lang="ts">
  import pkg from "number-to-words";
  import { onMount } from "svelte";
  const { toWords } = pkg;

  const numberToWords = (number: number) => {
    return toWords(number);
  };
 
  export let year: number = new Date().getFullYear();
  export let yearWords: string = numberToWords(year);
  let loading = true;

  onMount(() => {
    if (location.search) {
      const params = new URLSearchParams(location.search);
      const yearParam = params.get("year");
      if (yearParam) {
        year = parseInt(yearParam);
        yearWords = numberToWords(year);
      }
    }

    loading = false;
  });
</script>

<div class="flex items-center justify-center mt-10">
  <div class="block max-w-sm px-3 p-6 border rounded-lg shadow bg-gray-800 border-gray-700">
    <h5 class="mb-2 text-2xl font-bold tracking-tight text-white">How to say this year?</h5>
    <p class="font-normal text-gray-400">
      Type the year in the input field and get the correct pronunciation in English.
    </p>
    <p class="mb-0.5 text-gray-400 opacity-30">Butttt, yes you can also say any number 😭😅</p>

    <hr class="my-4 border-gray-700">

    {#if loading}
      <div class="h-10 bg-gray-200 rounded-md dark:bg-gray-700 mb-4"></div>
      <div class="h-10 bg-gray-200 rounded-md dark:bg-gray-700"></div>
    {:else}
      <input
        type="number"
        class="w-full px-4 py-2 mb-4 border rounded-lg bg-gray-800 border-gray-700 text-gray-200 focus:outline-none focus:shadow-outline"
        placeholder="Type the year here"
        bind:value={year}
        on:input={() => yearWords = numberToWords(year)}
      />

      <input
        type="text"
        disabled
        class="w-full px-4 py-2 border rounded-lg bg-gray-800 border-gray-700 text-gray-200 focus:outline-none focus:shadow-outline"
        value={yearWords}
      />
    {/if}
  </div>
  
  <div class="fixed md:absolute bottom-0 sm:bottom-auto right-0 md:top-0 z-10 gap-4 p-4">
    <a href="https://www.buymeacoffee.com/steellgold" class="hover:opacity-75 transition-opacity duration-300" target="_blank">
      <img class="h-10" src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="150" height="40" />
    </a>
  </div>
</div>

<div class="mt-6 text-center text-gray-400">
  <p>Made with ❤️ by <a class="text-gray-200" href="https://github.com/Steellgold">Steellgold</a></p>
</div>