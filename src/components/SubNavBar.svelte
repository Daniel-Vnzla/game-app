<script>
	import NavBar from './NavBar.svelte';
	import Game from './Game.svelte';
	export let game = {};
</script>


<div class="sub-navbar">
	<a href="/Game/{game.id}" class="portada">
		<img src={game.background_image} alt="game">
		<div class="info">
			<h2 class="title">{game.name}</h2>
			<p class="released">Released: {game.released}</p>
		</div>
	</a>
	<div class="navbar">
		<NavBar />
	</div>
	
</div>

<style>
	.sub-navbar {
		position: relative;
		height: 700px;
		width: 100%;

	}

	.sub-navbar .portada {
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
	}

	.sub-navbar .portada img {
		position: absolute;
		background: #d2d2d2;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: center;
	}

	.sub-navbar .portada::before {
		z-index: 1;
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		content: "";
		background: rgba(0,0,0, .5);
	}

	.sub-navbar .portada .info {
		color: #fff;
		font-size: 2rem;
		position: absolute;
		bottom: 90px;
		left: 20px;
		z-index: 2;
	}

	.sub-navbar .portada .released {
		color: #d2d2d2;
		font-weight: bold;
		font-size: 1rem;
	}

	.navbar {
		position: relative;
		z-index: 4;
	}


</style>