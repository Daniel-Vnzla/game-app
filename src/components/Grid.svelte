<script>
	import Game from './Game.svelte';
	export let games = [];
</script>


<div class="container">
	<h2 class="title">Games</h2>
	<div class="grid">
		{#each games as game, index}
			<Game title={game.name} released={game.released} img={game.background_image} id={game.id}/>
		{/each}
	</div>
</div>


<style>
	.container {
		width: 95%;
		margin: 0 auto;
	}
	.container .title {
		color: #f2f2f2;
		font-size: 2.5rem;
		margin-top: 70px;
	}

	.container .grid {
		display: grid;
		margin: 0 auto;
		max-width: 1400px;
		grid-template-columns: repeat(3, 1fr);
		grid-gap: 10px;
	}

</style>