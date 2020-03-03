<script>
	import { onMount } from 'svelte';
	import Gallery from './Gallery.svelte';
	import Landing from './Landing.svelte';

	let pageNum = 1;
	let page;

	onMount(async () => {
		const res = await fetch(`https://api.harvardartmuseums.org/image?apikey=API_KEY&page=${pageNum}`);
		page = await res.json();
		if (res.ok) {
			return page;
		} else {
			throw new Error('Fetch failed');
		}
	})

  async function getPhotos() {
    const res = await fetch(`https://api.harvardartmuseums.org/image?apikey=API_KEY&page=${pageNum}`);
		page = await res.json();
		if (res.ok) {
			return page;
		} else {
			throw new Error('Fetch failed');
		}
	}

	let user = {hasEntered: true};

	function handleToggle(event) {
		user.hasEntered = event.user
	};

	function handleNewPage(event) {
		pageNum = event.detail.newNum
		page = getPhotos();
	}

</script>

{#if user.hasEntered}
	<Landing on:toggle={handleToggle} user={user}/>
{:else}
	{#await page}
		<p>...waiting</p>
	{:then page}
		<Gallery records={page.records} on:newPage={handleNewPage} pageNum={pageNum}/>
	{:catch error}
		<p style="color: red">{error.message}</p>
	{/await}
{/if}

<style>
</style>