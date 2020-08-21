<script>
	import Image from './image.svelte';

	export let images = [];
	export let alt;

</script>

<div class="screenShots">
	<h2 class="title">ScreenShots</h2>
	<div class="images">
	{#each images as img}
		<Image img={img.image} alt={alt}/>
	{/each}
</div>
</div>

<style>
	.screenShots {
		margin: 0 auto;
		margin-top: 50px;
		width: 90%;
		padding-bottom: 50px;
	}

	.screenShots .title {
		font-size: 2rem;
		color: #f2f2f2;
	}

	.screenShots .images {
		display: grid;
		grid-gap: 5px;
		grid-template-columns: repeat(4,1fr);
	}

</style>