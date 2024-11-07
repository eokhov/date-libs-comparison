<script>
  const { children } = $props();
</script>

<main>
  {@render children()}
</main>

<style>
  main {
    width: 1600px;
    margin: 0 auto;
  }
</style>