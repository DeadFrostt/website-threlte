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
              VANTA.FOG({
                  el: "#vanta-bg",
                  mouseControls: true,
                  touchControls: true,
                  gyroControls: false,
                  minHeight: 200.00,
                  minWidth: 200.00,
                  highlightColor: 0xffffff,
                  midtoneColor: 0x0,
                  lowlightColor: 0xff0000,
                  baseColor: 0x90909,
                  blurFactor: 0.50,
                  zoom: 0.90
              });
          } else {
              console.error('VANTA is not defined');
          }
      };

      Promise.all([
        loadScript('https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js'),
        loadScript('https://cdn.jsdelivr.net/npm/vanta/dist/vanta.fog.min.js')      ])
      .then(() => {
          initializeVanta();
      })
      .catch(error => {
          console.error('Failed to load Vanta or Three.js script:', error);
      });
  });
</script>

<style>
#vanta-bg {
  width: 100%;
  height: 100vh;
}
</style>

<div id="vanta-bg"></div>
