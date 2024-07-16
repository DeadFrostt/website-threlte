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
