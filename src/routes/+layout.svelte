<!-- SveliteKit(Svelte5): /src/routes/+layout.svelte -->
<script lang="ts">
	import favicon from '$lib/assets/tepbar-favicon.png';
    import FooterMain from '$lib/components/()/FooterMain.svelte';
	import HeaderMain from '$lib/components/()/HeaderMain.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<!-- <link rel="preconnect" href="https://fonts.googleapis.com">
  	<link rel="preconnect" href="https://fonts.gstatic.com">
  	<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;700&display=swap" rel="stylesheet"> -->
</svelte:head>

<HeaderMain />
{@render children?.()}
<FooterMain />

<style>
	    /* =============================================================== */
    /* === ส่วนที่เพิ่มเข้ามา: นิยาม @font-face สำหรับ Sarabun Font === */
    /* =============================================================== */

    /* sarabun-100 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 100;
        src: url('/fonts/sarabun-v17-latin_thai-100.woff2') format('woff2');
    }
    /* sarabun-200 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 200;
        src: url('/fonts/sarabun-v17-latin_thai-200.woff2') format('woff2');
    }
    /* sarabun-300 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 300;
        src: url('/fonts/sarabun-v17-latin_thai-300.woff2') format('woff2');
    }
    /* sarabun-regular - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 400;
        src: url('/fonts/sarabun-v17-latin_thai-regular.woff2') format('woff2');
    }
    /* sarabun-500 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 500;
        src: url('/fonts/sarabun-v17-latin_thai-500.woff2') format('woff2');
    }
    /* sarabun-600 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 600;
        src: url('/fonts/sarabun-v17-latin_thai-600.woff2') format('woff2');
    }
    /* sarabun-700 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 700;
        src: url('/fonts/sarabun-v17-latin_thai-700.woff2') format('woff2');
    }
    /* sarabun-800 - latin_thai */
    @font-face {
        font-display: swap;
        font-family: 'Sarabun';
        font-style: normal;
        font-weight: 800;
        src: url('/fonts/sarabun-v17-latin_thai-800.woff2') format('woff2');
    }

    /* =============================================================== */
    /* ===                 ส่วน CSS เดิมของคุณ                      === */
    /* =============================================================== */
</style>