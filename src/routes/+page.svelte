<script lang="ts">
	import AdvancedSearchModal from '$lib/components/AdvancedSearchModal.svelte';

	let showModal = true;
</script>

<header class="w-full border-b border-b-slate-200">
	<div class="max-w-7xl mx-auto px-8 py-2 flex items-center justify-between">
		<!-- Logo -->
		<h1 class="text-3xl font-bold text-rose-700">Realator.Sveltent</h1>

		<!-- Search -->
		<input
			class="border-2 border-rose-700 rounded-full px-4 py-2 focus:outline-none placeholder:text-gray-400 transition duration-150 text-lg w-96"
			placeholder="Search..."
		/>

		<!-- Advanced Search(Filters) -->
		<button
			on:click={() => (showModal = true)}
			class="text-white bg-rose-700 hover:bg-rose-800 focus:ring-4 focus:ring-rose-300 font-medium rounded-lg text-base px-4 py-1.5"
		>
			Advanced Search
		</button>
	</div>
</header>

<AdvancedSearchModal {showModal} />

<style>
	@import '../app.css';
</style>
