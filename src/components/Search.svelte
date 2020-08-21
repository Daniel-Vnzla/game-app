<script>
	import Loading from './Loading.svelte';
	
	let value = "";

	const searchGame = async (search) => {
		if (search && search.length >= 2) {
			const game = await fetch(`https://api.rawg.io/api/games?search=${search}`);
			const data = await game.json();
			return data.results;
		} else return [];
		
	}
</script>


<div class="searcher" >
	<input class="search" autocomplete="off" type="text" name="search" bind:value placeholder="Search a game">
	<div class="games" class:active={value && value.length >= 2 } >
		{#await searchGame(value)}
		<div class="loading">
			<Loading title="GAMEZ" color="#fff"/>
		</div>
		{:then games}
			{#if games}
				{#each games as game}
					<a href="/Game/{game.id}" class="game">	
						<div class="img" loading=lazy>
							<img src={game.background_image} alt={game.name}>
						</div>
						<div class="details">
							<h4 class="title">{game.name}</h4>
							<p class="released">released: {game.released}</p>
						</div>
				</a>
				{/each}
			{:else}
				<p class="noResults">No Results</p>
			{/if}
		{:catch error}
				<p>{error}</p>
		{/await }
	</div>
</div> 


<style>
	.loading {
		display: grid;
		place-items: center;
		height: 150px;
	}

	.searcher {
		color: #f2f2f2;
		position: relative;
		z-index: 1000;
	}

	.searcher .search {
		width: 600px;
		outline: none;
		color: #fff;
		font-size: 1.5rem;
		border-style: none;
		background: rgba(210,210,210, .4);
		padding: 10px 20px;
	}

	.searcher .search::placeholder {
		color: rgb(255,255,255, .7);
	}

	.searcher .games {
		position: absolute;
		padding: 5px;
		top: 60px;
		left: 0;
		width: 100%; 
		max-height: 600px;
		background: #2A3C5A;
		overflow: auto;
		visibility: hidden;
	}

	.searcher .games::-webkit-scrollbar {
		width: .81rem;
	}

	.searcher .games::-webkit-scrollbar-thumb {
		background: #fff;
		border-radius: 50px;
		border: solid 4px #394e70;
	}

	.searcher .games::-webkit-scrollbar-track {
		background: #394e70;
	}

	.searcher .active {
		visibility: visible; 
	}

	.searcher .games .game {
		position: relative; 
		display: grid;
		grid-template-columns: 1fr 2fr;
		color: #fff;
		font-size: 1.4rem;
		grid-gap: 10px;
		min-height: 100px;
	}

	.searcher .games .game .img img{
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.searcher .games .game:hover {
		filter: brightness(1.2);
	} 

	.searcher .games .game .details .title {
		font-size: 1.4rem;
		line-height: 1.4rem;
	}

	.searcher .games .game .details .released {
		font-size: 1rem;
	}

</style>
