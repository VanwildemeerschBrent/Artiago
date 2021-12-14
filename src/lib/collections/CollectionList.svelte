<script>
	import ArtworkCard from '$lib/collections/ArtworkCard.svelte';
	import Loader from '$lib/core/Loader.svelte';
	let paginatedData = null;
	let artworks = [];
	fetch('https://api.artic.edu/api/v1/artworks')
		.then((response) => response.json())
		.then((response) => {
			paginatedData = response;
			artworks = response.data;
			console.log(artworks);
		});
</script>

{#if paginatedData}
	<div class="collection-list">
		{#each artworks as artwork}
			<ArtworkCard title={artwork.title} imageID={artwork.image_id}/>
		{/each}
	</div>
{:else}
	<Loader />
{/if}

<style>
	.collection-list {
		width: 100%;
		height: fit-content;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-between;
		align-items: center;
	}
</style>
