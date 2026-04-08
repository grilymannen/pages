<script>
  // import { toRadians } from "$lib/utils";
  const widgetData = [
    {
      post: 'https://www.tumblr.com/slugfishh/734075615509086208/sait',
      src: 'imgs/sait.jpg',
      artist: '@slugfishh'
    },
    {
      post: 'https://www.tumblr.com/rain-mantis/798154938937212928/i-finally-tried-out-wigglypaint-its-very-fun-but',
      src: 'imgs/saint_wigglypaint.webp',
      artist: '@rain-mantis',
    }
  ]
  let breathing = $state(false);
  let interval;
  let increment = 0;
  let yOffset = $state(0);
  let currentWidget = widgetData[1];

  function startBreathe() {
    console.log('staret')
    breathing = true;
    interval = setInterval(animateBreathing, 1);
  }
  function endBreathe() {
    breathing = false;
    clearInterval(interval);
  }
  function animateBreathing() {
    increment++;
    yOffset = Math.sin(increment * 0.02) * 5;
  }
</script>
<main class='w-screen h-screen grid grid-rows-[50px_1fr_50px] *:text-neutral-200 '>
  <div></div>
  <div class='h-full flex items-center justify-center gap-4'>
    <h1 class='text-4xl font-bold'>Hello, I am grily!</h1>
    <div class="w-80">
      <img src={currentWidget.src} alt='main widget' style='top: {yOffset}px;' class='relative shadow-2xl'>
      <a 
        href={currentWidget.post} 
        class='text-blue-300 underline' 
        target='_blank' 
        rel='external'>stolen with respect from {currentWidget.artist}</a>
    </div>
  </div>
  <div></div>
</main>

<aside class='fixed bottom-2 right-2 flex gap-4 *:bg-zinc-800 *:px-4 *:py-2 *:text-neutral-200 *:rounded-2xl *:shadow-2xl'>
  <button onclick={startBreathe} disabled={breathing} class:bg-amber-500={breathing}>Start</button>
  <button onclick={endBreathe} disabled={!breathing}>End</button>
</aside>

<style>

</style>