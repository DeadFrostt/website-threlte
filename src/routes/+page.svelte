<script>
  import Socials from '$lib/Socials.svelte';
  import CustomCursor from '$lib/CustomCursor.svelte';
  import Background from '$lib/Background.svelte';
</script>

<main>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;700&display=swap" rel="stylesheet">

  <div id="vanta-bg"></div>
  <div class="content-wrapper">
    <div class="container">
      <h1>DeadFrost</h1>
      <p>Hello, I'm DeadFrost, an Indian resident studying in the United States.<br>
      I'm passionate about programming, enjoy gaming, and have a love for movies.</p>
      <Socials />
      <h2 class="text-2xl font-semibold mb-2">What I am Listening To</h2>
      <div class="lastfm-iframe">
        <iframe 
          id="lastfm-iframe" 
          src="https://yaz.ninja/lastfm/harshil74?target=_blank" 
          frameborder="0" 
          scrolling="no" 
          style="width: 50%; height: 150px;" 
          title="Listening to music on Last.fm">
        </iframe>
      </div>
    </div>
  </div>
  <Background />
  <CustomCursor />
  <div class="footer">
    Made with 💖 and Threlte on SvelteKit
  </div>
</main>