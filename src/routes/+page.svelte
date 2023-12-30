<script lang="ts">
	import { onMount } from 'svelte';
	import '../app.css';
	import Door from './Door.svelte';
	import Sakooby from './Sakooby.svelte';
	import type { Rive } from '@rive-app/canvas';
	import { fade } from 'svelte/transition';
	import Ask from './Ask.svelte';
	import phone from '$lib/images/Phone.png?enhanced';

	let riveInstance: Rive;
	let whirlVisible = false;
	onMount(() => {
		const particles = document.getElementsByClassName('particle');
		for (let i = 0; i < particles.length; i++) {
			const randomValue = Math.floor(Math.random() * 100);
			const element = particles[i] as HTMLElement;
			element.style.left = `${randomValue}vw`;
			element.style.animationDelay = `${i / 2}s`;
		}
	});
	$: className = whirlVisible ? 'animate-fade animate-reverse animate-delay-[4300ms]' : '';
	let hasRun = false;
	let hidden = true;
	$: {
		if (whirlVisible && !hasRun) {
			setTimeout(() => {
				className += ' hidden ';
				hidden = false;
			}, 6000);
			hasRun = true;
		}
	}
</script>

<svelte:head>
	<title>Sakooby ❤️</title>
	<meta name="description" content="❤️" />
</svelte:head>

<div class="fixed inset-0 bg-black">
	{#each Array(100) as _, i}
		<div class="particle"></div>
	{/each}
	<enhanced:img
		id="ask"
		src={phone}
		alt="ask"
		class={hidden ? 'hidden' : 'block animate-fade animate-duration-1000'}
	/>
	<!-- {#if hidden} -->
	<!-- <Ask /> -->
	<!-- {/if} -->
	<div class={'fixed inset-0 flex items-center flex-col justify-center p-[15%] ' + className}>
		<Sakooby className="stroke-pink-300" />
		<Door bind:riveInstance bind:whirlVisible />
	</div>
</div>

<style>
	/* Set general particle attributes */
	.particle {
		width: 5px;
		height: 5px;
		/* background-color: white; */
		border-radius: 50%;
		position: absolute;
		bottom: 0;
		animation:
			particle-rise 10s linear infinite,
			particle-glow 1.5s ease-in-out alternate infinite,
			particle-random 10s linear infinite,
			color-change 1.5s ease-in-out alternate infinite;
	}

	@keyframes color-change {
		0% {
			background-color: black;
		}
		50% {
			background-color: white;
		}
		100% {
			background-color: black;
		}
	}

	/* Set particle path */
	@keyframes particle-rise {
		0% {
			bottom: 0;
		}
		100% {
			bottom: 100%;
		}
	}

	/* Set particle glow */
	@keyframes particle-glow {
		0% {
			opacity: 0;
		}
		25% {
			opacity: 1;
		}
		50% {
			box-shadow: 0 0 10px 5px rgba(255, 255, 255, 0.7);
		}
		75% {
			opacity: 1;
		}
		100% {
			opacity: 0;
			box-shadow: 0 0 2px 1px rgba(255, 255, 255, 0);
		}
	}

	/* Randomise particle movement */
	@keyframes particle-random {
		0% {
			transform: translate(0, 0);
		}
		10% {
			transform: translate(-5px, -10px);
		}
		20% {
			transform: translate(5px, -20px);
		}
		30% {
			transform: translate(-3px, -30px);
		}
		40% {
			transform: translate(3px, -40px);
		}
		50% {
			transform: translate(-2px, -50px);
		}
		60% {
			transform: translate(2px, -60px);
		}
		70% {
			transform: translate(-1px, -70px);
		}
		80% {
			transform: translate(1px, -80px);
		}
		90% {
			transform: translate(-0.5px, -90px);
		}
		100% {
			transform: translate(0.5px, -100px);
		}
	}
</style>
