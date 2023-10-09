<script lang='ts'>
	import { createEventDispatcher, onMount } from 'svelte';

	export let offline: boolean;

	const dispatch = createEventDispatcher();

	onMount(() => {
		offline = !navigator.onLine;
		window.addEventListener('offline', () => {
			offline = true;
			dispatch('offline');
		});
		window.addEventListener('online', () => {
			offline = false;
			dispatch('online');
		});
	});
</script>
