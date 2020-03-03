<script>
  let src;
  // const getPhotos = async (req, res) => {
  //   let records = await fetch('https://api.harvardartmuseums.org/image?q=width:>220&apikey=3b95e4a0-5c11-11ea-9b44-2df473addcc2')
  //   .then(res => res.json())
  //   .then(data => console.log(data))
  
  //   src = records.records[0].baseimageurl
  //   console.log(src)
  // }
  let promise = getPhotos();

  	async function getPhotos() {
    const res = await fetch('https://api.harvardartmuseums.org/image?q=width:>220&apikey=3b95e4a0-5c11-11ea-9b44-2df473addcc2');
    await console.log(res)
		const body = await res.json();
    await console.log(body)
    const src = body.records[0].baseimageurl
		if (res.ok) {
			return src;
		} else {
			throw new Error('Fetch failed');
		}
	}

</script>


<section>
  {#await promise}
    <p>...waiting</p>
  {:then number}
    <img {p} alt='gallery-collection'/>
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</section>


<style>

</style>