<script>
  import { onMount } from 'svelte';

  let hours = 0;
  let minutes = 0;
  let seconds = 0;

  // 次の日の0時0分0秒までの残り時間を計算する関数
  function calculateCountdown() {
    const now = new Date();
    const tomorrow = new Date(now.getFullYear(), now.getMonth(), now.getDate() + 1);
    const diff = tomorrow.getTime() - now.getTime(); // ミリ秒単位の差分

    hours = Math.floor(diff / 1000 / 60 / 60);
    minutes = Math.floor(diff / 1000 / 60) % 60;
    seconds = Math.floor(diff / 1000) % 60;
  }

  // コンポーネントがマウントされた後、1秒ごとにカウントダウンを更新
  onMount(() => {
    calculateCountdown();
    const interval = setInterval(calculateCountdown, 1000);

    return () => {
      clearInterval(interval); // コンポーネントのアンマウント時にインターバルをクリア
    };
  });
</script>

<div class="grid grid-flow-col gap-5 text-center auto-cols-max">
  <div class="flex flex-col">
    <span class="countdown font-mono text-5xl">
      <span style="--value:{hours};"></span>
    </span>
    hours
  </div> 
  <div class="flex flex-col">
    <span class="countdown font-mono text-5xl">
      <span style="--value:{minutes};"></span>
    </span>
    min
  </div>
  <div class="flex flex-col">
    <span class="countdown font-mono text-5xl">
      <span style="--value:{seconds};"></span>
    </span>
    sec
  </div>
</div>
