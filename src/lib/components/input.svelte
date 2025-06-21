<script lang="ts">
	import { cn } from '$lib/utils';
	import type { HTMLInputAttributes } from 'svelte/elements';

	interface Props extends HTMLInputAttributes {
		label?: string;
	}

	let { class: classname, label, value = $bindable(), ...props }: Props = $props();
	const uid = $props.id();
</script>

<div class="flex flex-col">
	{#if label}
		<label for={`${uid}-label`}>{label}</label>
	{/if}

	<input
		class={cn('h-10 border border-gray-300 px-2 outline-none', classname)}
		bind:value
		{...props}
	/>
</div>
