<script>
  import Countdown from "./Countdown.svelte";

  const afternoon = new Date()
  afternoon.setHours(12, 0 ,0 ,0);
  
  const workEnd = new Date()
  workEnd.setHours(18, 0 ,0 ,0);

  const todayEnd = new Date()
  todayEnd.setHours(23, 59 ,59 ,999);
</script>

<div class="grid place-items-center w-full h-screen">
  <Countdown title="Lunch" end={afternoon}/>
  <Countdown title="Work Time" end={workEnd}/>
  <Countdown title="Today" end={todayEnd}/>
</div>


<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
