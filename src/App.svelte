<script lang="ts">
	import DogsRandomDog from './DogsRandomDog.svelte';
	import DogsBreeds from './DogsBreeds.svelte';
	import Header from './Header.svelte';
	let title = 'Sample Svelte js Dogs';
</script>

<Header>
	<title>Home</title>
</Header>

<h1>{title}</h1>
<DogsRandomDog />
<DogsBreeds />

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

</style>
