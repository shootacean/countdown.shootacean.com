<script>
  import Countdown from "./Countdown.svelte";
</script>

<div class="grid place-items-center w-full h-screen">
  <main>
    <Countdown />
  </main>
</div>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
