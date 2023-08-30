<script lang="ts">
  import "../app.css";

  export let title: string = "Year to Words";
  export let siteName: string = "Get year to words";
  export let description: string = "Type the year in the input field and get the correct pronunciation in English.";
  export let url: string = "https://wordsyears.vercel.app";
  export let keywords: string = "sveltekit, svelte, sveltekit starter, sveltekit template, sveltekit typescript, sveltekit tailwindcss";
  export let color: string = "#0F172A";
</script>

<title>{title}</title>
<meta name="description" content={description} />
<meta name="keywords" content={keywords} />
<meta name="og:title" content={title} />
<meta name="og:site_name" content={siteName} />
<meta name="og:description" content={description} />
<meta name="og:url" content={url} />
<meta name="og:type" content="website" />
<meta name="twitter:site" content="@Steellgold" />
<meta name="twitter:creator" content="@Steellgold" />
<meta name="twitter:title" content={title} />
<meta name="twitter:description" content={description} />
<meta name="theme-color" content={color} />

<slot />