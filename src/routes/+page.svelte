<script>
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
  let currentWidget = widgetData[1];
</script>
<main class='w-screen h-screen grid grid-rows-[50px_1fr_50px] *:text-neutral-200 '>
  <div></div>
  <div class='h-full flex items-center justify-center gap-4'>
    <h1 class='text-4xl font-bold'>Hello, I am grily!</h1>
    <div class="w-80">
      <img src={currentWidget.src} alt='main widget'>
      <a 
        href={currentWidget.post} 
        class='text-blue-300 underline' 
        target='_blank' 
        rel='external'>stolen with respect from {currentWidget.artist}</a>
    </div>
  </div>
  <div></div>
</main>


<style>

</style>