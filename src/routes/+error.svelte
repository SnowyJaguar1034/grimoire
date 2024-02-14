<script lang="ts">
	import { page } from '$app/stores';
</script>

{#if $page.error}
	<div class="flex h-full w-full flex-col items-center gap-20 align-top">
		<h1 class="text-center text-4xl font-bold">Incantation failed :(</h1>
		<div class="flex w-max items-center">
			<div class="text-6xl md:mr-6">🧙 🪄</div>
			<div class="mockup-browser max-w-[12rem] border border-base-300 sm:max-w-xs md:max-w-sm">
				<div class="mockup-browser-toolbar">
					<div class="input border border-base-300">grimoire error</div>
				</div>
				<div class="flex justify-center border-t border-base-300 px-4 py-16">
					<span class="text-center text-6xl font-bold text-base-300">💥</span>
				</div>
			</div>
		</div>
		<div class="mx-auto w-fit p-4">
			<h2 class="text-2xl">Error message:</h2>
			<code class="text-xl">
				{$page.error.message}
			</code>
		</div>
	</div>
{/if}
