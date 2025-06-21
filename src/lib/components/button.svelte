<script lang="ts">
	import { cn } from '$lib/utils';
	import type { HTMLButtonAttributes } from 'svelte/elements';

	interface Props extends HTMLButtonAttributes {}

	let { class: classname, children, type = 'button', ...props }: Props = $props();
</script>

<button
	class={cn('flex h-10 cursor-pointer items-center gap-2 border border-gray-300 px-4', classname)}
	{type}
	{...props}
>
	{@render children?.()}
</button>
