<script>
  const widgetData = [
    {post: 'https://www.tumblr.com/slugfishh/734075615509086208/sait', src: 'imgs/sait.jpg', artist: 'slugfishh' }
  ]
  let currentWidget = widgetData[0];
</script>
<main class='w-screen h-screen grid grid-rows-[50px_1fr_50px]'>
  <div></div>
  <div class='h-full flex items-center justify-center gap-4'>
    <h1>Hello, I am grily!</h1>
    <div class="h-full grow-0">
      <img src={currentWidget.src} alt='main widget' class='h-1/4'>
      <a href={currentWidget.post} target='_blank' rel='external'>stolen with respect from {currentWidget.artist}</a>
    </div>
  </div>
  <div></div>
</main>


<style>

</style>