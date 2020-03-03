<script>
	import Photo from './Photo.svelte';
</script>


<main>
	<header>
		<h1>Harvard's Art Museum Collection</h1>
	</header>
	<Photo />
</main>

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