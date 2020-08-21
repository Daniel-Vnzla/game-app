<script>
	import axios from 'axios';
	import router from 'page';
	import Principal from './routes/Principal.svelte';
	import GameInfo from './routes/GameInfo.svelte';
	import Loading from './components/Loading.svelte';

	const getGames = async() => {
		const games = await fetch("https://api.rawg.io/api/games?page_size=40");
		const data = await games.json(); 
		const allGames = data.results;
		return allGames;
	}

	let page;
	let params;
	router('/',() =>  router.redirect('/Home') );
	router('/Home',() =>  page = Principal );
	router('/Game/:id',(ctx, next) => {
		params = ctx.params;
		next();
	},() => {page = GameInfo} );

	router.start();
</script>

<main class="main">
	{#await getGames()}
		<div class="loadingScreen">
			<Loading title="GAMEZ" color="#fff"/>
		</div>
	{:then games}
		{#if page === Principal}
			<svelte:component this={page} games={games} />
		{:else}
			<svelte:component this={page} games={games} params={params}/>
		{/if}
	{:catch error}
		<p>{error}</p>
	{/await}
</main>




<style>
	.main {
		width: 100%;
		background: #2A3C5A;
	}
	.loadingScreen {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		background: #2A3C5A;
	}
</style>
