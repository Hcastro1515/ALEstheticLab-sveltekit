<script lang="ts">
	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell,
		Checkbox
	} from 'flowbite-svelte';

	import { Pagination } from 'flowbite-svelte';

	export let data: any;

	const itemsPerPage: number = 10;
	let currentPage: number = 1;

	const totalPages: number = Math.ceil(data.length / itemsPerPage);

	interface Helper {
		start: number;
		end: number;
		total: number;
	}

	let helper: Helper = { start: 1, end: 10, total: 100 };

	function updatePagination(page: number): void {
		currentPage = page;
		helper.start = (currentPage - 1) * itemsPerPage + 1;
		helper.end = Math.min(currentPage * itemsPerPage, data.length);
	}

	function previous(): void {
		if (currentPage > 1) {
			updatePagination(currentPage - 1);
		}
	}

	function next(): void {
		if (currentPage < totalPages) {
			updatePagination(currentPage + 1);
		}
	}
</script>

<Table hoverable={true}>
	<TableHead>
		<TableHeadCell class="!p-4">
			<Checkbox />
		</TableHeadCell>
		<TableHeadCell>Nombre</TableHeadCell>
		<TableHeadCell>Servicio</TableHeadCell>
		<TableHeadCell>Agente</TableHeadCell>
		<TableHeadCell>Precio</TableHeadCell>
		<TableHeadCell>
			<span class="sr-only"> Edit </span>
		</TableHeadCell>
	</TableHead>
	<TableBody>
		{#each data.slice(helper.start - 1, helper.end) as customer (customer.id)}
			<TableBodyRow>
				<TableBodyCell class="!p-4">
					<Checkbox />
				</TableBodyCell>
				<TableBodyCell>{customer.nombre}</TableBodyCell>
				<TableBodyCell>{customer.servicio}</TableBodyCell>
				<TableBodyCell>{customer.agente}</TableBodyCell>
				<TableBodyCell>{customer.price}</TableBodyCell>
				<TableBodyCell>{customer.time}</TableBodyCell>
			</TableBodyRow>
		{/each}
	</TableBody>
</Table>

<div class="flex flex-col items-center justify-center gap-2">
	<Pagination table>
		<!-- {#if currentPage > 1} -->
		<span slot="prev" on:click={previous}>prev</span>
		<!-- {/if} -->

		<!-- {#if currentPage < totalPages} -->
		<span slot="next" on:click={next}>next</span>
		<!-- {/if} -->
	</Pagination>
</div>
