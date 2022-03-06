<script lang="ts">
	import { Configuration, PostsApi } from './app/core/api/generated/index';
	import { of, fromEvent } from 'rxjs';
	import {
		map,
		concatMap,
		switchMap,
		startWith,
		debounceTime,
	} from 'rxjs/operators';
	import { onMount$ } from 'svelte-rx';

	let inputElement;
	const conf = new Configuration({
		basePath:'https://jsonplaceholder.typicode.com',
	});
	const postsApi = new PostsApi(conf);
	const searchPosts = (query) => {
		return postsApi.getPosts({q:query,limit:10})
	};
	const posts = onMount$.pipe(
		debounceTime(100),
		concatMap(() =>
		fromEvent(inputElement, 'input').pipe(
			debounceTime(350),
			map((e:any) => e.target.value),
			switchMap((query) => {
			console.log('me at search input',query);
			if (!query) {
				return of([])
			}
			return searchPosts(query);
			}),
		),
		),
		startWith([]),
	);

</script>
<div class="post-list">
	<details>
		<summary class="h1">Posts</summary>
		<div>
			<label style='width: 100%'>
				<span>filter posts</span>
				<input
					bind:this="{inputElement}"
					value=""
					placeholder="search lorem ipsum" />
			</label>
			<ul>
				{#each $posts as post}
					<li>{post.title}</li>
				{/each}
			</ul>
		</div>
	</details>
</div>

<style>
  .post-list {
    width: 100%;
    text-align: center;
  }
</style>

