
<script>
	export let title = 'Loading';
	export let color = "#fff000";
</script>


	<div class="loading" style="--color: {color}">
		{title}
		<span class="ball"></span>
	</div>




<style>
	
	:root {
		--border: 3px;
		--circle: 100px;
		--color: #2A3C5A;
		--speed: 1300ms;
	}
	
	.loading {
		font-weight: bold;
		font-family: 'Poppins';
		position: relative;
		display: grid;
		place-items: center;
		height: 100%; 
		color: var(--color);
		text-shadow: 0 0 20px var(--color);
		width: var(--circle);
		height: var(--circle);
		font-size: calc( var(--circle) / 5.5);
		background: none;
		border-radius: 50%;
		border: var(--border) solid rgba(255,255,255, .4);
	}
	
	.loading::before {
		position: absolute;
		content: "";
		top: calc(0px - var(--border));
		left: calc(0px - var(--border));
		right: calc(0px - var(--border));
		bottom: calc(0px - var(--border));
		border: var(--border) solid transparent;
		border-top-color: var(--color);
		border-right-color: var(--color);
		border-radius: 50%;
		animation: circle var(--speed) infinite linear
	}
	
	.ball {
		position: relative;
		display: block;
		width: 50%;
		height: 4px;
		position: absolute;

		left: 50%;
		transform-origin: left;
		animation: circleBall var(--speed) infinite linear
	}
	
	.ball::before {
		position: absolute;
		content: "";
		width: 16px;
		height: 16px;
		top: calc(0px - var(--border) * 2);
		right: calc(0px - var(--border) * 3);
		box-shadow: 0 0 20px var(--color);
		border-radius: 50%;
		background: var(--color);
		
	}
	
	@keyframes circle {
		0%{
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg)
		}
	}
	
		@keyframes circleBall {
		0%{
			transform: rotate(50deg);
		}
		100% {
			transform: rotate(410deg)
		}
	}
</style>