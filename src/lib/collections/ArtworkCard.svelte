<script>
	export let title;
	export let imageID;

	const baseUrl = 'https://www.artic.edu/iiif/2';
	let noImageSrc = 'images/no_image.jpg';

	function onClickCard() {
		console.log('Clicked card');
	}
</script>

<div class="card" on:click={onClickCard}>
	{#if imageID}
		<img src={`${baseUrl}/${imageID}/full/843,/0/default.jpg`} alt="art_image" />
	{:else}
		<img src={noImageSrc} alt="art_image" />
	{/if}
	<h3>{title}</h3>
</div>

<style>
	.card {
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
		max-width: 300px;
		width: 300px;
		margin: 0.5;
		text-align: center;
		font-family: arial;
		background: white;
	}
	.card:hover {
		cursor: pointer;
	}

	img {
		width: 100%;
		max-height: 300px;
	}

	.card button {
		border: none;
		outline: 0;
		padding: 12px;
		color: white;
		background-color: #000;
		text-align: center;
		cursor: pointer;
		width: 100%;
		font-size: 18px;
	}

	.card button:hover {
		opacity: 0.7;
	}
</style>
