<script>
	import Gallery from './Gallery.svelte';
	import Landing from './Landing.svelte';

	let promise = getPhotos();

  async function getPhotos() {
    const res = await fetch(`https://api.harvardartmuseums.org/image?apikey=API_KEY`);
		const body = await res.json();
		if (res.ok) {
			return body;
		} else {
			throw new Error('Fetch failed');
		}
	}

	let user = {hasEntered: true};

	function handleToggle(event) {
		user.hasEntered = event.user
	};

</script>

{#if user.hasEntered}
	<Landing on:toggle={handleToggle} user={user}/>
{:else}
	{#await promise}
		<p>...waiting</p>
	{:then body}
		<Gallery records={body.records}/>
	{:catch error}
		<p style="color: red">{error.message}</p>
	{/await}
{/if}

<style>
</style>