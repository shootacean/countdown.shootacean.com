<div class="grid place-items-center w-full h-screen">
  <span class="countdown">
    <span style="--value:{value};"></span>
  </span>
</div>

<script>
  let value = 5;
  const timer = setInterval(() => {
    value -= 1;
  }, 1000);
  setTimeout(() => {
    clearInterval(timer);
  }, 5000);
</script>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
