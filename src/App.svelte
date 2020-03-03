<script>
	import Photo from './Photo.svelte';
	let promise = getPhotos();
	
	async function getPhotos() {
		const res = await fetch(`tutorial/random-number`);
		const text = await res.text();

		if (res.ok) {
			return text;
		} else {
			throw new Error(text);
		}
	}
	// const getPhotos = async (req, res) => {
  //   let records = await fetch('https://api.harvardartmuseums.org/image?q=width:>220&apikey=3b95e4a0-5c11-11ea-9b44-2df473addcc2')
  //   .then(res => res.json())
  //   .then(data => console.log(data))
  
  //   src = records.records[0].baseimageurl
  //   console.log(src)
  // }
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