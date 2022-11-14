<script lang="ts">
	import Body from "./components/Body.svelte";
	import Footer from "./components/Footer.svelte";
	import Header from "./components/Header.svelte";
</script>

<main>
	<Header />
	<Body />
	<Footer />
</main>

<style>
	main {
		display: flex;
		min-height: 100vh;
		flex-direction: column;
	}
</style>
