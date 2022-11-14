<script lang="ts">
	export let col;
	export let row;
	export let showGrid = false;
</script>

<div class="grid">
	<div class="row">
		{#each row as iRow, i}
			<input
				class="rowInput"
				type="checkbox"
				id={`row-${i}`}
				bind:checked={iRow}
			/>
		{/each}
	</div>
	<div class="col">
		{#each col as iCol, i}
			<input
				class="colInput"
				type="checkbox"
				id={`col-${i}`}
				bind:checked={iCol}
			/>
		{/each}
	</div>
	<div class="svg">
		<svg width="100%" height="961px">
			{#each col as offset, i}
				<line
					x1={i * 50 + 10}
					x2={i * 50 + 10}
					y1="10"
					y2="5000"
					stroke="white"
					stroke-width="2"
					stroke-dasharray={50}
					stroke-dashoffset={offset ? 50 : 0}
				/>
			{/each}

			{#each row as offset, i}
				<line
					x1="10"
					x2="5000"
					y1={i * 50 + 10}
					y2={i * 50 + 10}
					stroke="white"
					stroke-width="2"
					stroke-dasharray="50"
					stroke-dashoffset={offset ? 50 : 0}
				/>
			{/each}

			{#if showGrid}
				{#each col as _, i}
					{#each row as _, j}
						<circle
							fill="red"
							opacity="0.8"
							cx={i * 50 + 10}
							cy={j * 50 + 10}
							r={3}
						/>
					{/each}
				{/each}
			{/if}

			Sorry, your browser does not support inline SVG.
		</svg>
	</div>
</div>

<style>
	.colInput {
		margin-right: 32.7px;
	}
	.colInput:last-child {
		margin-right: 0px;
	}
	.row {
		grid-area: rowBox;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.col {
		grid-area: colBox;
		/* display: flex;
		justify-content: space-between; */
	}
	.svg {
		grid-area: svgBox;
	}
	.grid {
		display: grid;
		flex-grow: 1;
		grid-template-columns: 25px auto;
		grid-template-areas:
			"  .    colBox"
			"rowBox svgBox";
		margin-bottom: 50px;
	}
</style>
