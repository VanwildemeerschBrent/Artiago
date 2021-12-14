<script>
	import ArtworkCard from '$lib/collections/artwork_card.svelte';

	let paginatedData = [];
	fetch('https://api.artic.edu/api/v1/artworks')
		.then((response) => response.json())
		.then((response) => (paginatedData = response));
</script>

<h1>Collections list</h1>

{#each paginatedData.data[0] as artwork}
	<ArtworkCard />
{/each}
