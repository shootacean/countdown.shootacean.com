<script lang="ts">
  import { onMount } from 'svelte';


  // TODO : 編集できるようにする
  export let title: string = 'Countdown';
  export let end: Date = new Date(new Date().getFullYear(), new Date().getMonth(), new Date().getDate() + 1);

  let hours = 0;
  let minutes = 0;
  let seconds = 0;

  /**
   * カウントダウンを計算する
   * @returns void
   */
  function calculateCountdown() {
    const now = new Date();
    const diff = end.getTime() - now.getTime(); // ミリ秒単位の差分

    hours = Math.floor(diff / 1000 / 60 / 60);
    minutes = Math.floor(diff / 1000 / 60) % 60;
    seconds = Math.floor(diff / 1000) % 60;

    if (hours === 0 && minutes === 0 && seconds === 0) {
      // タイマーの完了通知を送る
      const message = `Finished : ${title}`
      if (!("Notification" in window)) {
        console.debug("This browser does not support desktop notification");
      } else if (Notification.permission === 'granted') {
        console.debug("notifiction already granted");
        new Notification(message);
      } else {
        Notification.requestPermission().then((permission) => {
          console.debug("notifiction request result", permission);
          if (permission === 'granted') {
            new Notification(message);
          }
        });
      }
    }
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

<div>
  <h2>{title}</h2>
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
</div>
