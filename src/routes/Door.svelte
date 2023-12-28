<script lang="ts">
	import { onMount } from 'svelte';

	onMount(async () => {
		const { Rive, Layout, Fit, Alignment } = await import('@rive-app/canvas');
		const canvasElement = document.getElementById('rive_canvas') as HTMLCanvasElement;

		let r = new Rive({
			onLoad: () => {
				r.resizeDrawingSurfaceToCanvas();
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
	});
</script>

<div>
	<canvas id="rive_canvas" class=" min-w-full min-h-full"></canvas>
</div>
