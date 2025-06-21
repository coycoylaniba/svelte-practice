<script lang="ts">
	import Button from '$lib/components/button.svelte';
	import Input from '$lib/components/input.svelte';
	import { cn } from '$lib/utils';

	interface Todo {
		name: string;
		done: boolean;
	}

	let todos: Todo[] = $state([]);
	let name = $state('');

	function add(event: SubmitEvent) {
		event.preventDefault();

		if (name.length === 0) return;

		todos.push({ name, done: false });
		name = '';
	}

	function remove(index: number) {
		todos = todos.filter((_t, i) => index !== i);
	}
</script>

<h1>Todo Page</h1>

<div class="w-64">
	{#each todos as todo, index}
		<div class="flex items-center gap-2">
			<input type="checkbox" bind:checked={todo.done} />
			<span class={cn(todo.done && 'line-through')}>{todo.name}</span>
			<button type="button" onclick={() => remove(index)}>Remove</button>
		</div>
	{/each}

	<form onsubmit={add}>
		<Input label="Name" id="name" name="name" placeholder="Enter todo name" bind:value={name} />
		<Button type="submit">Save</Button>
	</form>
</div>
