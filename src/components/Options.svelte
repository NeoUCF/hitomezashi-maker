<script lang="ts">
	import { createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher<{
		randomize: number;
		gridPoints: void;
	}>();

	let probability = 0.5;

	const handleRandomize = () => {
		dispatch("randomize", probability);
	};

	const handleGridPoints = () => {
		dispatch("gridPoints");
	};
</script>

<div>
	<button on:click={handleRandomize}>Randomize</button>
	<button on:click={handleGridPoints}>Show Grid Points</button>
</div>

<style>
	div {
		display: flex;
		justify-content: space-around;
		margin: 30px;
	}
</style>
