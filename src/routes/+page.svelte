<script lang="ts">
	import { Button, Heading, Modal, Label, Input, Checkbox, Select} from 'flowbite-svelte';
	import Datepicker from '../components/datepicker.svelte';
	import CustomTable from '../components/custom-table.svelte';
	import { customerData } from '$lib/customers';

	let date = new Date();

	function showCurrentDate() {
		let day = date.getDate();
		let month = date.getMonth() + 1;
		let year = date.getFullYear();
		let currentDate = day + '/' + month + '/' + year;

		return currentDate;
	}

	let showModal = false;
	let services = [
		{ value: 'pestanas', name: 'Pestanas' },
		{ value: 'ms-relax', name: 'Masajes Relajantes' },
		{ value: 'ms-manual', name: 'Masajes Manuales' },
		{ value: 'm-basico', name: 'Maquillaje basico' },
		{ value: 'm-boda', name: 'Maquillaje de Boda' },
		{ value: 'pestanas', name: 'Pestanas' }
	];

	let personal = [
		{value: 'nairoby', name: 'Nairoby'},
		{value: 'benjaming', name: 'Benjaming'},
		{value: 'erika', name: 'Erika'},
		{value: 'Yomari', name: 'Yomari'}
	]
</script>

<Modal bind:open={showModal} size="md" autoclose={true} class="w-full">
	<form class="flex flex-col space-y-6" action="#">
		<h3 class="mb-4 text-xl font-medium text-gray-900 dark:text-white">Agendar Cita de Cliente</h3>
		<Label class="space-y-2">
			<span>Nomber</span>
			<Input type="text" name="name" placeholder="Nombre Del Cliente" required />
		</Label>
		<Label class="space-y-2">
			<span>Telefono / Cell</span>
			<Input type="text" name="cel" placeholder="888-888-8888" required />
		</Label>
		<Label>
			<span>Fecha de servicio</span>
			<Datepicker />
		</Label>
		<Label class="space-y-2">
			<span>Servicio</span>
			<Select items={services} placeholder="Servicios" />
		</Label>
		<Label>
			<span>Personal</span>
			<Select items={personal} placeholder="Naoriby" />
		</Label>
		<Label class="space-y-2">
			<span>Precio</span>
			<Input type="number" name="price" placeholder="$3,500" required />
		</Label>

		<Button type="submit" class="w-full1">Agendar</Button>
	</form>
</Modal>

<div class="my-10">
	<Heading tag="h1" customSize="text-4xl font-extrabold  md:text-5xl lg:text-6xl"
		>Welcome AlaestheticLab</Heading
	>
	<p class="mt-2 text-black">
		Today is <span class="font-semibold">{showCurrentDate()}</span> Lets prepare for an amazing day!
	</p>
</div>

<div class="space-y-3">
	<div class="w-full shadow-md rounded-t-md p-6 flex justify-between items-center">
		<div class="text-center inline-flex">
			<p class="text-xl">Hoy tenemos <span class="font-semibold">21</span> citas en agenda</p>
		</div>
		<Button on:click={() => (showModal = true)}>Agendar Cita</Button>
	</div>
	<div class="w-full shadow-md rounded-b-md">
		<CustomTable data={customerData} />
	</div>
</div>
