<script>
	let col = Array(30);
	let row = Array(20);
</script>

<div class="grid">
	<div class="row">
		{#each row as _, i}
			<input class="rowInput" type="checkbox" id={`row-${i}`} />
		{/each}
	</div>
	<div class="col">
		{#each col as _, i}
			<input class="colInput" type="checkbox" id={`col-${i}`} />
		{/each}
	</div>
	<div class="svg">
		<svg width="100%" height="967px">
			{#each col as _, i}
				<line
					x1={i * 50.3 + 10}
					x2={i * 50.3 + 10}
					y1="10"
					y2="5000"
					stroke="white"
					stroke-width="2"
				/>
			{/each}

			{#each row as _, i}
				<line
					x1="10"
					x2="5000"
					y1={i * 50.3 + 10}
					y2={i * 50.3 + 10}
					stroke="white"
					stroke-width="2"
				/>
			{/each}

			Sorry, your browser does not support inline SVG.
		</svg>
	</div>
</div>

<style>
	/* div {
		overflow: scroll;
		width: 90rem;
	} */
	.colInput {
	}
	.row {
		grid-area: rowBox;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.col {
		grid-area: colBox;
		display: flex;
		justify-content: space-between;
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
	}
</style>
