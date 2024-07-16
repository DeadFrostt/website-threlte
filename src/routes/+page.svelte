<script>
	import Socials from '$lib/Socials.svelte';
</script>

<main>
	<div class="content-wrapper">
		<div class="container">
			<h1>DeadFrost</h1>
			<p>
				Hello, I'm DeadFrost, an Indian resident studying in the United States.<br />
				I'm passionate about programming, enjoy gaming, and have a love for movies.
			</p>
			<Socials />
			<h2 class="text-2xl font-semibold mb-2">What I am Listening To</h2>
			<div class="lastfm-iframe">
				<iframe
					id="lastfm-iframe"
					src="https://yaz.ninja/lastfm/harshil74?target=_blank"
					frameborder="0"
					scrolling="no"
					style="width: 50%; height: 150px;"
					title="Listening to music on Last.fm"
				>
				</iframe>
			</div>
		</div>
	</div>
	<div class="footer">Made with 💖 and Threlte on SvelteKit</div>
</main>

<style>
	.content-wrapper {
		display: flex;
		justify-content: center; /* Center content horizontally */
		align-items: center; /* Center content vertically */
		width: 100%;
		height: 100vh; /* Full viewport height */
	}

	.container {
		text-align: left; /* Align text to the left */
		max-width: 800px;
		width: 100%;
		padding: 20px;
		box-sizing: border-box;
	}

	h1 {
		font-size: 48px; /* Set font size for the title */
		font-weight: bold; /* Bold font */
		margin: 0 0 24px; /* Add some space below the title */
		animation: fadeIn 2s; /* Fade in animation */
	}

	p {
		font-size: 18px; /* Set font size for the text */
		margin: 0 0 16px; /* Add some space below the text */
		animation: fadeIn 2s; /* Fade in animation */
	}

	.footer {
		position: fixed;
		bottom: 10px;
		right: 10px;
		font-size: 0.875rem;
		color: #666;
		animation: fadeIn 2s; /* Fade in animation */
	}

	.text-2xl {
		animation: fadeIn 2s; /* Fade in animation */
	}
</style>
