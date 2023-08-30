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
  <div class="block max-w-sm p-6 border rounded-lg shadow bg-gray-800 border-gray-700">
    <h5 class="mb-2 text-2xl font-bold tracking-tight text-white">How to say this year?</h5>
    <p class="font-normal text-gray-400">
      Type the year in the input field and get the correct pronunciation in English.
    </p>
    <p class="mb-0.5 text-gray-400 opacity-30">Butttt, yes you can also say any number 😭😅</p>

    <hr class="my-4 border-gray-300 dark:border-gray-700">

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
</div>