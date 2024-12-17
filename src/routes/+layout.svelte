<script lang="ts">
	import Header from '$lib/components/Header.svelte';
	import '../app.css';
	let { children } = $props();

	import data from '../lib/data/data.json';
	// take json and transform it into an object
	const body = data;
	const menu = {
		projects: 'Proyectos MOT',
		contact: 'Contacto',
		home: 'Espai MOT'
	};
</script>

<Header {menu} />
{@render children()}
