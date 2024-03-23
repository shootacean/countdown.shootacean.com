<script lang="ts">
  import Countdown from "./Countdown.svelte";

  /**
   * 現在の年齢
   */
  export let currentAge: number = 29;

  /**
   * 寿命
   * @see https://eikaiwa.dmm.com/uknow/questions/45687/
   */
   const LIFESPAN = 81.41;
  /**
   * 健康寿命
   * @see https://eikaiwa.dmm.com/uknow/questions/31349/
   */
  const HEALTHY_LIFESPAN = 72.68;

</script>

<section>
  <h2 class="text-left">Lifespan ( {LIFESPAN} years old )</h2>
  <progress class="progress progress-primary w-full" value={LIFESPAN-currentAge} max={LIFESPAN}></progress>
  <Countdown end={new Date(new Date().getFullYear() + LIFESPAN-currentAge, new Date().getMonth(), new Date().getDate())} />
</section>

<section class="mt-8">
  <h2 class="text-left">Healthy Lifespan ( {HEALTHY_LIFESPAN} years old )</h2>
  <progress class="progress progress-success w-full" value={HEALTHY_LIFESPAN-currentAge} max={HEALTHY_LIFESPAN}></progress>
  <Countdown end={new Date(new Date().getFullYear() + HEALTHY_LIFESPAN-currentAge, new Date().getMonth(), new Date().getDate())} />
</section>


