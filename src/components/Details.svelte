<script>
	export let plataform = [];
	export let generes = [];
</script>

<div class="details">
	<ul class="plataform">
		<h2>Plataform</h2>
		<div class="wrapper">
			{#each plataform as plataform}
			<li>{plataform.platform.name}</li>
			{/each}
		</div>
	</ul>
	<ul class="generes">
		<h2>Generes</h2>
		<div class="wrapper">
			{#each generes as generes}
			<li>{generes.name}</li>
			{/each}
		</div>
	</ul>
</div>


<style>
	.sub-navbar .details {
		padding: 20px;
	}

	.sub-navbar .details .generes {
		margin-top: 20px;
	}

	.sub-navbar .details .plataform .wrapper {
		display: flex;
	}

	.sub-navbar .details .generes .wrapper {
		display: flex;
	}

	.sub-navbar .details .generes li{
		color: #f2f2f2;
		background: #6b94c9;
		padding: 5px 10px;
		border-radius: 5px;
		margin: 5px;
		width: max-content;
		font-weight: bold;
	}

	.sub-navbar .details .plataform li {
		color: #f2f2f2;
		background: #6b94c9;
		padding: 5px 10px;
		border-radius: 5px;
		margin: 5px;
		width: max-content;
		font-weight: bold;
	}
</style>