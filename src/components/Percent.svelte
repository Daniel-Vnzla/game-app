<script>
	export let percent = 15.23;
	percent = Math.floor(percent);
	export let radio = '35px';
	export let stroke = '4px';
	export let toolTip = "tooltip";
</script>

<div data-tooltip={toolTip} class="progress" style={`--radio: ${radio}; --percent: ${percent}; --stroke-width: ${stroke}`}>
	<svg class="progress-bar">
		<circle cy={radio} cx={radio} r={radio}></circle>
		<circle cy={radio} cx={radio} r={radio}></circle>
	</svg>
	<h4 class="percent"> 
	{percent}%
	</h4>
</div>





<style>
	
	* {
		margin: 0;
		padding: 0;
	}	

	 .progress::before {
	 	font-weight: bold;
		position: absolute;
    content: attr(data-tooltip);
    top: -5px;
    left: 50%;
    width: max-content;
    transform: translate(-50%, -100%);
    font-size: 1rem;
    border-radius: 5px;
    background: #2a3c5a;
    padding: 2px 8px;
    visibility: hidden;
	}
	
	.progress:hover::before {
		visibility: visible;
	}

	:root {
		--radio: 30px;
		--stroke-width: 2px;
		--perimetre: calc(var(--radio) * 2 * 3.14);
	}
	
	.progress {
		position: relative;
		width: calc(var(--radio) * 2 + var(--stroke-width));
		height: calc(var(--radio) * 2 + var(--stroke-width));
	}
	.percent {
		position: absolute;
		font-size: calc(var(--radio) / 2);
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		color: #fff;
	}
	
	
	
	.progress-bar {
		width: calc(var(--radio) * 2 + var(--stroke-width));;
		height: calc(var(--radio) * 2 + var(--stroke-width));;
	}
	
	.progress-bar circle {
		fill: none;
		width: 100%;
		height: 100%;
		stroke: rgba(255,255,255, .3);
		stroke-width: var(--stroke-width);
		stroke-linecap: round;
		transform: translate(calc(var(--stroke-width) / 2),calc(var(--stroke-width) / 2));
	}

	.progress-bar circle:nth-child(2) {
		stroke-dashoffset: var(--perimetre); 
		stroke-dasharray: var(--perimetre);
		
	}
	
	.progress-bar circle:nth-child(2) {
		stroke-dashoffset: calc(var(--perimetre) - (var(--perimetre) * var(--percent)) / 100);
		stroke: #779BD8;
	} 

</style>
