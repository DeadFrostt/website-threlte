<script>
	import CustomCursor from '$lib/CustomCursor.svelte';
	import Background from '$lib/Background.svelte';
</script>

<svelte:head>
	<link
		rel="stylesheet"
		href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
	/>
	<link
		href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<main>
	<div id="vanta-bg"></div>

	<slot />

	<Background />
	<CustomCursor />
</main>

<style>
	#vanta-bg {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
		z-index: -1;
	}
</style>
