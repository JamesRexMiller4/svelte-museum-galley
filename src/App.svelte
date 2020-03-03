<script>
	import Photo from './Photo.svelte';
	import Landing from './Landing.svelte';

	let user = {hasEntered: true};

	function handleToggle(event) {
		user.hasEntered = event.user
	};

</script>

{#if user.hasEntered}
	<Landing on:toggle={handleToggle} user={user}/>
{:else}
	<main>
		<header>
			<h1>Harvard's Art Museum Collection</h1>
		</header>
		<Photo />
	</main>
{/if}

<style>
	main {
		width: 100vw;
		height: 100vh;
		margin: 0;
		background-image: url('../images/art-gallery-background-img.jpg');
		background-repeat: no-repeat;
		background-size: cover;
	}

	header {
		height: 20vh;
	}

	h1 {
		font-family: 'Open Sans';
		color: white;
		font-size: 2.5rem;
		padding: 40px;
	}
</style>