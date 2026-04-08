<script>
  import { onMount } from 'svelte'
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
  let interval;
  let increment = 0;
  let rotation = $state({x: 0, y: 0});
  let yOffset = $state(0);
  let currentWidget = widgetData[1];

  
  onMount(() => {
    startBreathe();
    
    const widget = document.getElementById('widget');
    widget.addEventListener('mousemove', handleMouseMove);
    widget.addEventListener('mouseleave', handleMouseLeave);
  });
  function handleMouseLeave() {
    rotation.x = 0;
    rotation.y = 0;
  }
  function handleMouseMove(event) {
    const maxDegrees = 25; // This is what looks good
    const widget = event.originalTarget;
    const size = {height: widget.clientHeight, width: widget.clientWidth};
    const ratioX = event.layerX / size.width;
    const ratioY = event.layerY / size.height;
    rotation.x = Math.sin((ratioX - 0.5)  ) * maxDegrees;
    rotation.y = Math.sin((ratioY - 0.5)) * maxDegrees;
  }
  function startBreathe() {
    interval = setInterval(animateBreathing, 1);
  }
  function endBreathe() {
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
    <div class='w-80 perspective-distant'>
      <div 
        class='relative hover:scale-110 hover:*:opacity-100'
        id='widget'
        style=
          'top: {yOffset}px; 
          transition: all 0.1s; 
          transform: rotateX({rotation.y}deg) rotateY({rotation.x}deg);'>
        
        <img 
          src={currentWidget.src} 
          alt='main widget'>
          <a 
            href={currentWidget.post} 
            class='text-blue-300 underline absolute top-1 text-center w-full bg-black/30 opacity-0 transition-opacity' 
            target='_blank' 
            rel='external'>↳ stolen with respect from {currentWidget.artist} </a>
        </div>
      
    </div>
  </div>
  <div></div>
</main>


<style>

</style>