<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<header class="flex h-12 items-center gap-4 border-b border-b-gray-300 px-4">
	<a href="/">Home</a>
	<a href="/todo">Todo</a>
	<a href="/calculator">Calculator</a>
</header>

<main class="flex flex-col">
	{@render children()}
</main>

<footer></footer>
