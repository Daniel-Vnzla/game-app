<script>
	export let id;

	const getGame = async () => {
		const game = await fetch(`https://api.rawg.io/api/games/${id}`);
		const data = await game.json();
		return data.description_raw;
	}
</script>

{#await getGame()}
	<p>Loading...</p>
{:then description}	
	<div class="description">
		<h2 class="title">Description</h2>
		{description}
	</div>
{/await}

<style>
	.description {
		font-size: 1.2rem;
		margin-top: 10px;
		padding-bottom: 10px;
	}
	.description p {
		margin: 10px;
	}
</style>