<script>
	import Door from './Door.svelte';
	import Sakooby from './Sakooby.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class=" bg-black flex items-center flex-col justify-center p-[15%]">
	<Sakooby className="stroke-pink-300" />
	<Door />
</div>
