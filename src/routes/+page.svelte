<script lang="ts">
	import '../app.css';
	import Door from './Door.svelte';
	import Sakooby from './Sakooby.svelte';
	import type { Rive } from '@rive-app/canvas';
	let riveInstance: Rive;
	

</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class=" fixed inset-0 bg-black flex items-center flex-col justify-center p-[15%]">
	<Sakooby className="stroke-pink-300" />
	<Door bind:riveInstance />
</div>
