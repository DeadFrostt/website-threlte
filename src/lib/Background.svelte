<script context="module" lang="ts">
    declare var VANTA: any;
  </script>

<script lang="ts">
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