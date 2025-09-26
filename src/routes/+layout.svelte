<script lang="ts">
	import favicon from '$lib/assets/tepbar-favicon.png';
    import FooterMain from '$lib/components/()/FooterMain.svelte';
	import HeaderMain from '$lib/components/()/HeaderMain.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<link rel="preconnect" href="https://fonts.googleapis.com">
  	<link rel="preconnect" href="https://fonts.gstatic.com">
  	<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;700&display=swap" rel="stylesheet">
</svelte:head>

<HeaderMain />
{@render children?.()}
<FooterMain />
