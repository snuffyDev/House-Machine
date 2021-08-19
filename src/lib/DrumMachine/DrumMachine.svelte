<script lang="ts">
	import { onMount } from 'svelte'

	import Pad from './Pad.svelte'

	export let length: number = 16
	let mounted
	let ROW_COUNT = 4
	type Row = boolean
	let grid: Row[][] = []
	let GRID_ITEM_NAMES = ['OHH', 'CHH', 'SNARE', 'KICK']
	const resizeGrid = (length) => {
		grid = [...Array(ROW_COUNT)].map(() =>
			[...Array(length)].map((d, i) => false)
		)

		console.log(grid)
	}
	onMount(() => {
		mounted = true
	})
	$: console.log(grid)
	$: if (mounted) resizeGrid(length)
</script>

<button on:click={() => length--}>-</button>{length}<button
	on:click={() => length++}>+</button>
<div class="drum-wrapper">
	{#each grid as row, p}
		<div class="drum-section">
			<div class="drum-label"><span>{GRID_ITEM_NAMES[p]}:</span></div>
			<div class="drum-grid" style={`--length: ${length}`}>
				{#each row as cell, i}
					<Pad bind:active={cell} />
				{/each}
			</div>
		</div>
	{/each}
</div>

<style lang="scss">
	$bg: #171724;

	.drum-label {
		position: sticky;
		left: 0;
		color: #f1f1f1;
		background: lighten($bg, 10%);
		height: 100%;
		width: 100%;
		display: flex;
		flex-wrap: nowrap;
		/* align-content: center; */
		justify-content: center;
		* {
			align-self: center;
			text-align: center;
		}
	}
	.drum-wrapper {
		overflow-x: scroll;
		width: 100%;
		background: $bg;
	}
	.drum-section {
		display: grid;
		grid-template-columns: 5rem 1fr;
		column-gap: 1rem;
		row-gap: 1rem;
	}
	.drum-grid {
		display: grid;
		grid-template-columns: repeat(var(--length), 3rem);
		gap: 0.5rem;
		padding: 0.5rem 1rem 0.5rem 0;
	}
</style>
