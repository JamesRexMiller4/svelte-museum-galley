<script>
	import Gallery from './Gallery.svelte';
	import Landing from './Landing.svelte';

	let user = {hasEntered: true};

	function handleToggle(event) {
		user.hasEntered = event.user
	};

</script>

{#if user.hasEntered}
	<Landing on:toggle={handleToggle} user={user}/>
{:else}
	<Gallery />
{/if}

<style>
</style>