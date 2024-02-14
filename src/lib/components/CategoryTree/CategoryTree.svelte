<script lang="ts">
	import Icon from '$lib/components/Icon/Icon.svelte';
	import type { Category } from '$lib/types/Category.type';

	export let categories: (Category & { children?: Category[] })[] | [] = [];
</script>

{#each categories as category (category.id)}
	<div class="flex flex-col">
		<div class="flex items-center">
			{#if !category.icon}
				<div
					class="my-auto h-4 w-4 rounded-full"
					style={`background-color: ${category?.color || '#a0a0a0'};`}
				/>
			{:else}
				<Icon name={category.icon} size={16} color={category?.color} />
			{/if}
			<a href={`/categories/${category.slug}`} class="link m-1 hover:text-primary"
				>{category.name}</a
			>
		</div>

		{#if category.children}
			{#each category.children as categoryChild (categoryChild.id)}
				<div class="ml-4 flex items-center">
					{#if !categoryChild.icon}
						<div
							class="my-auto h-4 w-4 rounded-full"
							style={`background-color: ${categoryChild?.color || '#a0a0a0'};`}
						/>
					{:else}
						<Icon name={categoryChild.icon} size={16} color={categoryChild?.color} />
					{/if}
					<a href={`/categories/${categoryChild.slug}`} class="link m-1 hover:text-primary"
						>{categoryChild.name}</a
					>
				</div>
			{/each}
		{/if}
	</div>
{/each}
