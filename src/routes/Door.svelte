<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { type Rive } from '@rive-app/canvas';
	export let riveInstance: Rive;
	onMount(async () => {
		const { Rive, Layout, Fit, Alignment, EventType } = await import('@rive-app/canvas');
		const canvasElement = document.getElementById('rive_canvas') as HTMLCanvasElement;
		riveInstance = new Rive({
			onLoad: () => {
				riveInstance.resizeDrawingSurfaceToCanvas();
			},
			src: '/door_opening_and_closing.riv',
			canvas: canvasElement,
			autoplay: true,
			artboard: 'New Artboard',
			stateMachines: 'State Machine 1',
			layout: new Layout({
				fit: Fit.Contain,
				alignment: Alignment.Center
			})
		});
		gsap.fromTo(
			canvasElement,
			{ opacity: 0 },
			{
				opacity: 1,
				duration: 2
				// delay: 1.5
			}
		);

		const timeoutId = setTimeout(() => {
			const smInputs = riveInstance.stateMachineInputs('State Machine 1');
			const toggleInput = smInputs[0];
			toggleInput.value = !toggleInput.value;
		}, 500);

		riveInstance.on(EventType.StateChange, (e) => {
			console.log(e);

			if (e.data == 'Fully Open') {
				const canvas_parent = document.getElementById('canvas_parent');
				gsap.to(canvas_parent, {
					scale: 20,
					duration: 8,
					delay: 3
				});
			}
		});
		// return () => {
		// 	clearTimeout(timeoutId);
		// 	riveInstance.cleanup();
		// };
	});
	function handleClick() {
		const smInputs = riveInstance.stateMachineInputs('State Machine 1');
		const toggleInput = smInputs[1];
		toggleInput.value = !toggleInput.value;
	}
</script>

<div id="canvas_parent" on:click={handleClick} on:keydown role="button" tabindex="0">
	<canvas id="rive_canvas" class=" min-w-full min-h-full"></canvas>
</div>
