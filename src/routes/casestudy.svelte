<script>
  import Splash from "../components/Splash.svelte";
  import StickyGallery from "../components/StickyGallery.svelte";
</script>

<style>
  main {
    background-color: #333;
  }
</style>

<svelte:head>
  <title>Case Study</title>
</svelte:head>
<main>
  <Splash text="Testing Case Study" instructions />
  <StickyGallery imageCount={4} basePath="/scroll/" />
  <Splash text="end" />
</main>
