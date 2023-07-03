<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import { Button } from 'flowbite-svelte';
	import { conversation_data } from './stores';
	import Persona from './Persona.svelte';
	import ConvMode from './ConvMode.svelte';
	import Script from './Script.svelte';
	import ConvType from './ConvType.svelte';
	import { Select, Label, Input, Helper } from 'flowbite-svelte';
	import SysMsg from './SysMsg.svelte';
	import { Navbar, NavBrand } from 'flowbite-svelte';
	import IntroOutro from './IntroOutro.svelte';
	import Free from './Free.svelte';
	import Gpt from './GPT.svelte';
	import SayThis from './SayThis.svelte';

	let conversations = ['user_number###ad'];
	let selected = '';
	let user_number = '';
	let filter = '';
	let info;

	async function getUserNumbers() {
		const response = await fetch('http://192.168.30.50:8998/list_conversations');
		let list_conversations = await response.json();
		conversations = list_conversations.message;
		return conversations;
	}

	async function get_objinfo() {
		let url = 'http://192.168.30.50:8998/obj_info/' + user_number.toString();
		console.log(user_number.toString());
		const response = await fetch(url);
		let obj_info = await response.json();
		info = JSON.parse(obj_info.message);
		conversation_data.set(info);
		console.log(info);
		//return conversations
	}

	function filterThis() {
		conversations = conversations.filter((item) => item.includes(filter)).map((item) => item);
	}

	$: {
		user_number = selected.split('###')[0].toString();
	}

	onMount(() => {
		getUserNumbers();
	});
</script>

<main>
	<Navbar>
		<NavBrand>
			<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
				ChippyBot Admin
			</span>
		</NavBrand>
	</Navbar>
	<div class="container mx-auto px-3">
		<Label for="filter" color="green" class="block mb-3 text-xl font-bold">Filter</Label>
		<Input
			id="filter"
			name="filter"
			color="green"
			bind:value={filter}
			on:input={filterThis}
			placeholder="Isi dengan filter"
		/>

		<div>
			<Label for="user_number" color="green" class="block mb-3 text-xl font-bold">User Number</Label
			>
			<Select name="user_number" id="user_number" bind:value={selected} on:change={get_objinfo}>
				{#each conversations as conv}
					<option class="text-xl" value={conv}>{conv}</option>
				{/each}
			</Select>
		</div>

		<div class="grid grid-cols-5">
			<Button class="bg-blue-500" on:click={getUserNumbers}>Refresh</Button>
			<Button color="red" class="bg-blue-500">Get Group</Button>
			<Button color="green" class="bg-blue-500" on:click={get_objinfo}>Get OBJ INFO</Button>
			<Button color="green" class="bg-blue-500">Toggle Maintenance</Button>
		</div>

		<br />

		<div class="flex items-center">
			<div class="bg-gray-300">
				<Persona />
				<ConvMode />
			</div>
			<div class="bg-gray-200">
				<Script />
				<ConvType />
			</div>
			<div>
				<Free />
			</div>
			<div>
				<Gpt />
			</div>
		</div>
		<div>
			<SayThis />
		</div>
		<div>
			<SysMsg />
		</div>
		<div>
			<IntroOutro />
		</div>

	</div>
</main>
