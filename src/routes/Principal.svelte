<script>
	import SubNavBar from '../components/SubNavBar.svelte';
	import Grid from '../components/Grid.svelte';

	export let games = [];

	//Generate Random Img
	let randomNum = Math.floor(Math.random() * games.length);
	const randomGame = games[randomNum];

</script>

<main class="main">
	<SubNavBar game={randomGame}/>
	<Grid games={games}/>
</main>

<style>
	.main {
		font-family: 'Poppins';
	}

</style>