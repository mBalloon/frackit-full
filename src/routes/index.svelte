<script context="module">
	export const prerender = true
</script>

<script>
	import Counter from '$lib/ui/Counter/index.svelte'
	import Welcome from '$lib/ui/Welcome.svelte'
	import List from '$lib/ui/List.svelte'
</script>

<template lang="pug">

	section
		h1
			.welcome
				Welcome

		List

		Counter

</template>

<style>
	section {
		display: flex;
		position: relative;
		flex-direction: column;

		justify-content: center;
		align-items: center;

		z-index: 1;
	}

	h1 {
		position: absolute;
		right: 0;
		left: 0;
		top: 0;

		width: 100%;

		margin: auto;

		pointer-events: none;
	}

	.welcome {
		position: relative;

		width: 100%;
	}
</style>
