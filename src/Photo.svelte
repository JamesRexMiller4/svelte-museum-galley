<script>
  let src;
  let promise = getPhotos();

  async function getPhotos() {
    const res = await fetch('https://api.harvardartmuseums.org/image?q=width:>220&apikey=3b95e4a0-5c11-11ea-9b44-2df473addcc2');
		const body = await res.json();
    src = body.records[4].baseimageurl
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
    <div>
      <img {src} alt='gallery-collection'/>
    </div>
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</section>


<style>
  div {
    width: 100vw;
    height: 100vh;
    text-align: center;
  }
  img {
    width: 220px;
    height: 324px;
    margin-top: 60px;
    margin-left: 10px;
  }
</style>