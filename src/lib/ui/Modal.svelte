<script>
	import { clickOutside } from '$lib/utils/clickOutside'
	import { showModal } from '$lib/stores/modal'
	import Button from '$lib/ui/Button.svelte'
	import { fly } from 'svelte/transition'

	export let title = 'Title'

	const hide = () => ($showModal = false)
</script>

<template lang="pug">

	+if('$showModal')
		
		.container
			.modal(use:clickOutside on:click_outside='{hide}' transition:fly!='{{y: 20}}')

				.x-icon(on:click='{hide}')
					svg(width="15" height="15" viewBox="0 0 64 64")
						path#x(d="M7 7L57 57M57 7L7 57" stroke="current-color" stroke-width="13" stroke-linecap="round")

				.title
					h1 {title}

				.content
					slot
						p Modal's are pretty great!

				.buttons
					
					Button(
						on:click='{hide}'
						bg='var(--dark-d)'
						bghover='var(--warn)'
						text='var(--light-b)'
						texthover='var(--always-dark)') Cancel
					
					Button(
						on:click='{hide}'
						bg='var(--brand-a)'
						text='var(--always-dark)') Confirm

				.close(on:click='{hide}')

</template>

<style>
	.container {
		position: absolute;
		top: 15rem;
		right: 0;
		left: 0;
	}
	.modal {
		position: relative;
		display: flex;
		flex-direction: column;

		width: 100%;
		min-width: 300px;
		max-width: min(90vw, 500px);
		margin: 2em auto;

		background: var(--light-b);
		box-shadow: 0 2px 10px 3px #00000022;
		border-radius: 10px;

		z-index: 200;
	}
	.title {
		min-height: max-content;

		line-height: 10px;
		font-size: 1em;
	}
	.content {
		line-height: 3em;

		border-top: 1px solid rgba(var(--dark-d-rgb), 0.1);
		border-bottom: 1px solid rgba(var(--dark-d-rgb), 0.1);
	}
	.buttons {
		margin-left: auto;
		width: max-content;
	}
	.content,
	.title,
	.buttons {
		padding: 0 1em;
	}
	.x-icon {
		position: absolute;
		right: 0;

		padding: 0.75em;

		cursor: pointer;

		transition: transform 0.5s;
	}
	#x {
		stroke: #bbbbbb;

		transition: stroke 0.25s;
	}
	.x-icon:hover #x {
		stroke: var(--warn);
	}
</style>
