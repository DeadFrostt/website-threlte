<script context="module" lang="ts">
  declare var VANTA: any;
</script>

<script lang="ts">
  import Socials from '$lib/Socials.svelte';
  import CustomCursor from '$lib/CustomCursor.svelte';
  import { onMount } from 'svelte';

  onMount(() => {
    const loadScript = (src: string) => {
      return new Promise<void>((resolve, reject) => {
        const script = document.createElement('script');
        script.src = src;
        script.onload = () => resolve();
        script.onerror = () => reject(new Error(`Failed to load script: ${src}`));
        document.head.appendChild(script);
      });
    };

    const initializeVanta = () => {
      if (typeof VANTA !== 'undefined') {
        VANTA.BIRDS({
          el: "#vanta-bg",
          mouseControls: true,
          touchControls: true,
          gyroControls: false,
          minHeight: 200.00,
          minWidth: 200.00,
          scale: 1.00,
          scaleMobile: 1.00,
          backgroundColor: 0x0,
          color1: 0xcf1f7b,
          color2: 0xffffff
        });
      } else {
        console.error('VANTA is not defined');
      }
    };

    Promise.all([
      loadScript('https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js'),
      loadScript('https://cdn.jsdelivr.net/npm/vanta/dist/vanta.birds.min.js')
    ])
    .then(() => {
      initializeVanta();
    })
    .catch(error => {
      console.error('Failed to load Vanta or Three.js script:', error);
    });
  });
</script>

<main>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" />
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;700&display=swap" rel="stylesheet">

  <div id="vanta-bg"></div>
  <div class="content-wrapper">
    <div class="container">
      <h1>DeadFrost</h1>
      <p>Hello, I'm DeadFrost, an Indian resident studying in the United States. <br>
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
  <CustomCursor />
  <div class="footer">
    Made with 💖 and Threlte on SvelteKit
  </div>
</main>
