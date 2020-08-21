<script>
	import axios from 'axios';

	import NavBar from '../components/NavBar.svelte';
	import Percent from '../components/Percent.svelte';
	import ScreenShots from '../components/ScreenShots.svelte';
	import Details from '../components/Details.svelte';
	import Description from '../components/Description.svelte';
	import Loading from '../components/Loading.svelte';
	
	export let games = [];
	export let params;

	$: id = params.id;

	const getGame = async (id) => {

		const game = games.find( game => game.id == id);
		
		if (!game) {
			const getGame = await axios(`https://api.rawg.io/api/games/${id}`);
			const newGame = getGame.data;
			return newGame;
		}
		else {
			return game;
		}
	
	}

	const getScreenShots = async (id) => {
		const screenShots = await axios(`https://api.rawg.io/api/games/${id}/screenshots`);
		return screenShots.data.results;
	}
	
</script>

{#await getGame(id)}
	<div class="loadingScreen">
		<Loading title="GAMEZ" color="#fff"/>
	</div>
{:then game}
	<div class="sub-navbar">
		<div class="navbar">
			<NavBar />
		</div>
		<div class="img">
			<img src={game.background_image} alt={game.name}>
		</div>
		<div class="section">
			<div class="info">
				<h2 class="title">{game.name}</h2>
				<p class="released">Released: {game.released}</p>
				<div class="video">
					<div class="head">
						<p class="title">Trailer:</p>
						<div class="ratings">
							<div class="wrapper">
								{#each game.ratings as rating}
								<div class="percents" >
									<Percent radio="30px" stroke="4px" percent={rating.percent} toolTip={rating.title}/>
								</div>		
								{/each}	
							</div>
						</div>
					</div>
					{#if game.clip}
						<video autobuffer autoloop loop controls>
							<source src={game.clip.clips['full']}>
							<object title={game.name} type="video/ogg" data="/media/video.oga" >
								<param name="autoplay" value="false">
								<param name="autoStart" value="0">
							</object>
						</video>
					{:else}
						<div class="noVideo">
							No Trailer
						</div>	
					{/if}
				
				</div>
			</div>
			<Details plataform={game.platforms} generes={game.genres} />
			<Description id={params.id} />
		</div>	
	</div>
	{#await getScreenShots(id)}
		<div class="loading">
			<Loading title="GAMEZ" color="#fff"/>
		</div>
	{:then img}
		<ScreenShots images={img} />		
	{/await}
{/await}




<style>

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

	.sub-navbar {
		position: relative;
		width: 100%;
		font-family: 'Poppins';
	}

	
	.sub-navbar .navbar {
		position: relative;
		z-index: 1000;
	}


	.sub-navbar .img {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		width: 100%;
		height: 100%;
	}

	.sub-navbar .img::before {
		z-index: 1;
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		content: "";
		background: rgba(0,0,0, .7);
	}

	.sub-navbar .img img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.sub-navbar .section {
		width: 90%;
		margin: 0 auto;
		margin-top: 50px;
		position: relative;
		color: #fff;
		z-index: 4;
	}
	
	.sub-navbar .section .info {
		line-height: 2rem;
		font-size: 2rem;
	}

	.sub-navbar .section .info .head{
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.sub-navbar .section .info .head .wrapper {
		display: flex;
	}

	.sub-navbar .section .info .head .wrapper .percents{
		position: relative;
		margin: 5px;
		cursor: pointer;
	}

	.sub-navbar .section .info .released{
		color: #d2d2d2;
		font-size: 1rem;
	}

	.sub-navbar .section .info .video {
		margin-top: 10px;
		width: 100%;
	}

	.sub-navbar .section .info .noVideo {
		width: 100%;
		background: #2A3C5A;
		display: grid;
		place-items: center;
		height: 400px;
	}

	.sub-navbar .section .info .video video{
		width: 100%;
	}

	.loading {
		padding: 50px 0;
		width: 100%;
		display: grid;
		place-items: center;
	}
	
</style>
