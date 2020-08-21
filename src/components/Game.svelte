
<script>
	export let title = "Title";
	export let released = "released";
	export let img;
	export let id = "id";
</script>

<a href="/Game/{id}" class="game">
	<div class="info">
		<h2 class="title">{title}</h2>
		<p class="released">Released: {released}</p>
	</div>
	<img class="img" loading=lazy src={img} alt="game">
</a>

<style>
	.game {
		position: relative;
		height: 400px;
		transition: 300ms;
	}

	.game:hover {
		transform: scale(1.01);
		z-index: 1000;
	}

	.game .info {
		color: #fff;
		font-size: 1.2rem;
		position: absolute;
		bottom: 90px;
		left: 20px;
		z-index: 2;
	}

	.game .info .released {
		color: #d2d2d2;
		font-weight: bold;
		font-size: .8em;
	}


	.game .img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.game::after {
		z-index: 1;
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		content: "";
		background: rgba(0,0,0, .5);
	} 
</style>