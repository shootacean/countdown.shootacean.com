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
  /**
   * 残りの活動時間(起きている時間)
   */
  const ACTIVITY_TIME = HEALTHY_LIFESPAN * (16/24);
  /**
   * 使用済みの活動時間
   */
   const USED_ACTIVITY_TIME = currentAge * (16/24);

  const now = new Date();

</script>

<section>
  <h2 class="text-left">Lifespan ( {LIFESPAN} years old )</h2>
  <progress class="progress progress-primary w-full" value={LIFESPAN-currentAge} max={LIFESPAN}></progress>
  <Countdown end={new Date(now.getFullYear() + LIFESPAN-currentAge, now.getMonth(), now.getDate())} />
</section>

<section class="mt-8">
  <h2 class="text-left">Healthy Lifespan ( {HEALTHY_LIFESPAN} years old )</h2>
  <progress class="progress progress-success w-full" value={HEALTHY_LIFESPAN - currentAge} max={HEALTHY_LIFESPAN}></progress>
  <Countdown end={new Date(now.getFullYear() + (HEALTHY_LIFESPAN - currentAge), now.getMonth(), now.getDate())} />
</section>

<section class="mt-8">
  <h2 class="text-left">Activity Time ( Healthy Lifespan * (16 / 24) )</h2>
  <progress class="progress progress-success w-full" value={ACTIVITY_TIME-USED_ACTIVITY_TIME} max={ACTIVITY_TIME}></progress>
  <Countdown end={new Date(now.getFullYear() + (ACTIVITY_TIME-USED_ACTIVITY_TIME), now.getMonth(), now.getDate())} />
</section>
