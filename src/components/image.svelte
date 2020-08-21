<script>
	export let img;
	export let alt;

	let open = false;
</script>

<div class="img" class:openImage={open} on:click={() => open = !open}>
	<img src={img} alt={alt} loading=lazy>
</div>

<style>
	.img img {
		width: 100%;
		height: 100%;
		cursor: pointer;
	}

	.img {
		transition: 300ms transform;
	}

	.img:hover {
		box-shadow: 4px 2px 5px #000;
		transform: scale(1.02);
	}

	.openImage {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		z-index: 1000;
	}

	.openImage::before {
		position: fixed;
		content: "Click to close";
		font-size: 1.2rem;
		top: 30px;
		left: 50%;
		transform: translate(-50%);
		background: #2A3C5A;
		padding: 0px 20px;
		color: #f2f2f2;
		border-radius: 5px;
		cursor: pointer;
	}
</style>