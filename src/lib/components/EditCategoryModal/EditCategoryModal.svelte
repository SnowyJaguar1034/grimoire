<script lang="ts">
	import EditCategoryForm from '../EditCategoryForm/EditCategoryForm.svelte';
	import { editCategoryStore as category } from '$lib/stores/edit-category.store';
	import { writable } from 'svelte/store';
	import { onMount } from 'svelte';

	const modal = writable<HTMLDialogElement>();

	onMount(() => {
		modal.set(document.getElementById('editCategoryModal') as HTMLDialogElement);
	});

	$: {
		if ($category?.id) {
			$modal.showModal();
		}
	}

	function closeModal() {
		category.set({});

		$modal.close();
	}
</script>

<dialog bind:this={$modal} id="editCategoryModal" class="modal">
	<form method="dialog" class="modal-box max-w-full sm:max-w-screen-md md:max-w-screen-md">
		<button
			type="button"
			on:click={closeModal}
			class="btn btn-circle btn-ghost btn-sm absolute right-2 top-2">✕</button
		>
		<h2 class="mb-4 text-lg font-bold">Edit category</h2>
		<EditCategoryForm {closeModal} />
	</form>
	<!-- <form method="dialog" class="modal-backdrop"> -->
	<button class="modal-backdrop" on:click={() => closeModal()}>close</button>
	<!-- </form> -->
</dialog>
