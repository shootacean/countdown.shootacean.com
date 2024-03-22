<script lang="ts">
  import Lifespan from "./Lifespan.svelte";
  // import Countdown from "./Countdown.svelte";

  const CURRENT_AGE = 29;

  // const debug = new Date()
  // debug.setSeconds(debug.getSeconds() + 3);

  // const afternoon = new Date()
  // afternoon.setHours(12, 0 ,0 ,0);
  
  // const workEnd = new Date()
  // workEnd.setHours(18, 0 ,0 ,0);

  // const todayEnd = new Date()
  // todayEnd.setHours(23, 59 ,59 ,999);

  // let timers = [
  //   { title: "Debug", end: debug },
  //   { title: "Lunch", end: afternoon },
  //   { title: "Work Time", end: workEnd },
  //   { title: "Today", end: todayEnd },
  // ];

  // type TimerEnd = Date | undefined;

  // let newTimerTitle = "";
  // let newTimerEnd: TimerEnd = undefined;

  // function addTimer() {
  //   if (newTimerTitle.trim() === "") {
  //     return;
  //   }
  //   if (newTimerEnd && newTimerEnd <= new Date()) {
  //     return;
  //   }
  //   const newTimer = {
  //     title: newTimerTitle,
  //     end: newTimerEnd!,
  //   }
  //   timers = [...timers, newTimer];
  //   newTimerTitle = "";
  //   newTimerEnd = undefined;
  // }
</script>

<div class="hero min-h-screen">
  <div class="hero-content text-center">
    <section class="max-w-md">
      <h1 class="text-5xl font-bold">Shootacean</h1>
      <div class="stats shadow my-8">
        <div class="stat">
          <div class="stat-title">Age</div>
          <div class="stat-value">{CURRENT_AGE}</div>
        </div>
        <div class="stat">
          <div class="stat-title">Biological Gender</div>
          <div class="stat-value">Man</div>
        </div>
        <div class="stat">
          <div class="stat-title">Country</div>
          <div class="stat-value">Japan</div>
        </div>
      </div>
      <Lifespan currentAge={CURRENT_AGE}/>
    </section>
  </div>
</div>

<!-- 
<div class="grid place-items-center w-full h-screen">
  <div class="card w-96 bg-primary text-primary-content">
    <div class="card-body">
      <h2 class="card-title">Add Timer</h2>
      <label class="input input-primary flex items-center gap-2">
        Name
        <input type="text" class="grow" placeholder="Daisy" bind:value={newTimerTitle}/>
      </label>
      <label class="input input-bordered flex items-center gap-2">
        End Time
        <input type="time" class="grow" placeholder="daisy@site.com" bind:value={newTimerEnd}/>
      </label>
      <div class="card-actions justify-end">
        <button class="btn" on:click={addTimer}>Add</button>
      </div>
    </div>
  </div>
  {#each timers as timer}
    <Countdown title={timer.title} end={timer.end}/>
  {/each}
</div>
-->

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
