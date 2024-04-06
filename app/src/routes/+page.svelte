<script lang="ts">
	import { useQuery } from '@sanity/svelte-loader';
	import Card from '../components/Card.svelte';
	import Welcome from '../components/Welcome.svelte';
	import type { PageData } from './$types';

	export let data: PageData;
	const q = useQuery(data);

	$: ({ data: posts } = $q);
</script>

<h1 class="text-3xl font-bold underline">
  Hello world!
</h1>

<div class="grid md:grid-cols-2">
	<div>
		<h2 class="text-2xl font-bold">Welcome to the blog</h2>
		<p class="text-lg">
			Welcome to the blog! Here you'll find all the latest posts from our team.
		</p>
	</div>
	<div>
		<img src="/images/hero.jpg" alt="Hero image" class="w-full h-full object-cover" />
	</div>

</div>

<section>
	{#if posts.length}
		{#each posts as post}
			<Card {post} />
		{/each}
	{:else}
		<Welcome />
	{/if}
</section>


<h1 class="text-3xl font-bold underline">
  Hello world!
</h1>