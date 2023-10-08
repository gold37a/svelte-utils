<script>
	import { createEventDispatcher, onMount } from 'svelte';
	import { offline } from '$lib/stores.js';

	const dispatch = createEventDispatcher();

	onMount(() => {
		window.addEventListener('offline', () => {
			dispatch('offline');
			$offline = true;
		});
		window.addEventListener('online', () => {
			dispatch('online');
			$offline = true;
		});
	});
</script>
