<script lang="ts">
	import { char, createRegExp, exactly, oneOrMore } from "magic-regexp";

	const reg = createRegExp(oneOrMore(char).after("/src/routes").before(exactly("/+")));

	const routes = [
		...new Set(
			Object.entries(import.meta.glob("/**/+*"))
				.map((entry) => reg.exec(entry[0]))
				.map((match) => match?.[0]),
		),
	];
	console.log("🚀 ~ routes:", routes);
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<ul>
	{#each routes as route}
		<li>
			<a href={route}>{route}</a>
		</li>
	{/each}
</ul>
