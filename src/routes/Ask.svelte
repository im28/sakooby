<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	export let className: string;

	onMount(() => {
		const paths = document.querySelectorAll('path');
		paths.forEach((path, index) => {
			const length = path.getTotalLength();
			gsap.fromTo(
				path,
				{ strokeDasharray: length, strokeDashoffset: length, strokeWidth: 4 },
				{
					strokeWidth: 4,
					strokeDashoffset: length * 2,
					duration: 2,
					ease: 'power1.inOut',
					delay: index * 1
				}
			);
		});
	});
</script>

