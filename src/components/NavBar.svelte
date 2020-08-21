<script>
	import Search from './Search.svelte';
</script>


<nav class="navbar"> 
	<div class="container">
		<a href="/Home" class="title"><h1>GAMEZ</h1></a>
		<Search />
	</div>
</nav>

<style>

	.navbar {
		position: relative;
		width: 100%;
		height: 80px;
		z-index: 1000;
	}

	.navbar .container {
		width: 90%;
		height: 100%;
		margin: 0 auto;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.navbar .title {
		font-size: 1.8rem;
		color: #fff;
	}

</style> 