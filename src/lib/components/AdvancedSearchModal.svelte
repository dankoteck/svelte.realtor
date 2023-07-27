<script lang="ts">
	import Modal from './Modal.svelte';
	import { conditions, propertyTypes, rentStatus } from '$lib/data';

	// Props
	export let showModal: boolean;

	// Methods
	function updateFilter(key: string, value: string | number) {
		console.log(key, value);
	}
</script>

<Modal {showModal}>
	<div
		slot="header"
		class="sticky top-0 bg-white border-b border-b-slate-200 z-10 flex items-center justify-between px-6 py-2"
	>
		<h2 class="text-xl font-medium">Advanced Search (Filters)</h2>
		<span class="cursor-pointer font-light text-4xl text-gray-700 hover:text-black">&times;</span>
	</div>

	<!-- Content -->
	<div class="px-6 overflow-y-auto max-h-[calc(80vh-71px)]">
		<div class="flex flex-col">
			<div class="border-b border-b-slate-200 py-6 flex flex-col gap-4">
				<h3 class="text-xl font-medium">Status</h3>

				<div class="grid grid-cols-2 gap-3">
					{#each rentStatus as status}
						<label class="flex items-center cursor-pointer w-fit">
							<input
								type="checkbox"
								on:change={() => updateFilter('status', status.value)}
								class="mr-3 w-6 h-6 outline-none ring-0"
							/>
							<span class="text-lg">{status.label}</span>
						</label>
					{/each}
				</div>
			</div>

			<div class="border-b border-b-slate-200 py-6 flex flex-col gap-4">
				<h3 class="text-xl font-medium">Baths and Beds</h3>

				<div class="flex flex-col gap-8">
					{#each ['baths', 'beds'] as kind}
						<div class="flex flex-col gap-4">
							<h4 class="text-lg text-gray-900">
								{kind.charAt(0).toUpperCase() + kind.slice(1)}
							</h4>
							<div class="flex items-center gap-4">
								{#each { length: 8 } as _, i}
									{#if i < 7}
										<button
											class="py-2 px-4 rounded-full transition duration-150 hover:bg-black hover:text-white border border-slate-200"
											>{i + 1}</button
										>
									{:else}
										<button
											class="py-2 px-4 rounded-full transition duration-150 hover:bg-black hover:text-white border border-slate-200"
											>{i + 1}+</button
										>
									{/if}
								{/each}
							</div>
						</div>
					{/each}
				</div>
			</div>

			<div class="border-b border-b-slate-200 py-6 flex flex-col gap-4">
				<h3 class="text-xl font-medium">Types</h3>

				<div class="grid grid-cols-2 gap-3">
					{#each propertyTypes as type}
						<label class="flex items-center cursor-pointer w-fit">
							<input
								type="checkbox"
								on:change={() => updateFilter('status', type.value)}
								class="mr-3 w-6 h-6 outline-none ring-0"
							/>
							<span class="text-lg">{type.label}</span>
						</label>
					{/each}
				</div>
			</div>

			<div class="border-b border-b-slate-200 py-6 flex flex-col gap-4">
				<h3 class="text-xl font-medium">Pets</h3>

				<div class="space-y-4">
					<div class="flex items-center justify-between">
						<span class="text-lg">Cats</span>
						<label class="flex items-center relative cursor-pointer">
							<input type="checkbox" value="" class="sr-only peer" />
							<div
								class="w-[60px] h-8 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-7 after:w-7 after:transition-all peer-checked:bg-blue-600"
							/>
						</label>
					</div>

					<div class="flex items-center justify-between">
						<span class="text-lg">Dogs</span>
						<label class="flex items-center relative cursor-pointer">
							<input type="checkbox" value="" class="sr-only peer" />
							<div
								class="w-[60px] h-8 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-7 after:w-7 after:transition-all peer-checked:bg-blue-600"
							/>
						</label>
					</div>
				</div>
			</div>

			<div class="border-b border-b-slate-200 py-6 flex flex-col gap-4">
				<h3 class="text-xl font-medium">Conditions</h3>

				<div class="grid grid-cols-2 gap-3">
					{#each conditions as cond}
						<label class="flex items-center cursor-pointer w-fit">
							<input
								type="checkbox"
								on:change={() => updateFilter('status', cond.value)}
								class="mr-3 w-6 h-6 outline-none ring-0"
							/>
							<span class="text-lg">{cond.label}</span>
						</label>
					{/each}
				</div>
			</div>
		</div>
	</div>

	<!-- Footer -->
	<div
		slot="footer"
		class="sticky bottom-0 bg-white z-10 border-t border-t-slate-200 flex items-center justify-between gap-4 px-6 py-4"
	>
		<button class="border border-slate-200 rounded-lg px-4 py-1.5">Cancel</button>
		<button
			class="hover:text-white text-black hover:bg-rose-700 transition duration-150 border border-rose-700 rounded-lg px-4 py-1.5"
			>Apply</button
		>
	</div>
</Modal>
