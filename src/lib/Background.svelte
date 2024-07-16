<script context="module" lang="ts">
	declare var VANTA: any;
</script>

<script lang="ts">
	import { onMount } from 'svelte';

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
				el: '#vanta-bg',
				mouseControls: true,
				touchControls: true,
				gyroControls: false,
				minHeight: 200.0,
				minWidth: 200.0,
				highlightColor: 0xffffff,
				midtoneColor: 0x0,
				lowlightColor: 0xff0000,
				baseColor: 0x90909,
				blurFactor: 0.5,
				zoom: 0.9,
				speed: 0.2
			});
		} else {
			console.error('VANTA is not defined');
		}
	};

	// vanta cannot load without three loaded
	// so instead, we load three before loading vanta
	//
	// before Promise.all was being used which runs all promises simultaneously,
	// when in this case, that should be run in sequence
	const import_modules = async () => {
		await loadScript('https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js');
		await loadScript('https://cdn.jsdelivr.net/npm/vanta/dist/vanta.fog.min.js');
	};

	onMount(() => {
		import_modules().then(initializeVanta).catch(console.error);
	});
</script>

<div id="vanta-bg"></div>

<style>
	#vanta-bg {
		width: 100vw;
		height: 100vh;
	}
</style>
