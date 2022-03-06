<script lang="ts">
	import DogsRandomDog from './DogsRandomDog.svelte';
	import DogsBreeds from './DogsBreeds.svelte';
	import Header from './Header.svelte';
	import Posts from './ApiClientPostsSample.svelte';

	let title = 'Sample Svelte js Dogs';

</script>
<section>
	<Header />
</section>
<section>
	<h1>{title}</h1>
	<DogsRandomDog />
	<DogsBreeds />
	<Posts />
</section>
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
