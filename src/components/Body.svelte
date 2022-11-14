<script lang="ts">
	import Grid from "./Grid.svelte";
	import Options from "./Options.svelte";

	let col = Array<boolean>(30).fill(false);
	let row = Array<boolean>(20).fill(false);

	const handleRandomize = (e: CustomEvent<number>) => {
		col = col.map((_) => Math.random() < e.detail);
		row = row.map((_) => Math.random() < e.detail);
	};
	// $: console.log(col);
</script>

<div>
	<Options on:randomize={handleRandomize} on:gridPoints />
	<Grid {col} {row} />
</div>
