<script>
	import { onMount } from 'svelte'

	let bars = [
		{ color: '#F9D1E4', width: '1' },
		{ color: '#E4DF00', width: '2' },
		{ color: '#37AD60', width: '1' },
		{ color: '#F9D1E4', width: '1' }
	]

	function setBar() {
		bars = bars.map((bar) => ({
			width: Math.random() * 10,
			color: bar.color
		}))
	}

	export const animate = false

	onMount(() => {
		if (animate) {
			setInterval(setBar, 5000)
		}
	})
</script>

<div class="background">
	<div class="bar-left" />
	<div class="wrapper--inner">
		{#each bars as bar}
			<div class="bar" style="background-color: {bar.color}; flex-grow: {bar.width}" />
		{/each}
	</div>
	<div class="bar-right" />
</div>

<style lang="scss">
	.background {
		inset: 0;
		z-index: -10;
		position: fixed;
		height: 100vh;
		display: flex;
	}

	.wrapper--inner {
		margin: 0 auto;
		width: var(--width-inner);
		display: flex;
		justify-content: center;
	}

	.bar {
		min-width: 10px;
		transition: all ease-in-out 0.5s;
	}

	.bar-left {
		height: 100%;
		flex-grow: 1;
		background-color: var(--green);
	}

	.bar-right {
		height: 100%;
		flex-grow: 1;
		background-color: var(--yellow);
	}
</style>
