<!-- SvelteKit(Svelte5): $lib/components/()/HeaderMain.svelte -->
 <script lang="ts">
	import { fade } from 'svelte/transition';

	// State สำหรับควบคุมการเปิด/ปิดเมนูมือถือ
	let isMobileMenuOpen = $state(false);

	function toggleMenu() {
		isMobileMenuOpen = !isMobileMenuOpen;
	}
</script>

<header>
	<div class="header-logo-section">
		<a href="/" class="logo-link">
			<div class="logo-wrapper">
				<img src="/images/logo/tepbar-logo.png" alt="tepbar logo" />
				<h2>TEP BAR</h2>
			</div>
		</a>
		<div class="tagline-wrapper">
			<p>The Cultural Bar of Thailand | Since 2015</p>
		</div>
	</div>

	<div class="header-nav-section">
		<hr />
		<nav class="desktop-nav">
			<a href="/">Home</a>
			<a href="/menu">Menu</a>
			<a href="/reservation" style="cursor: pointer;">Reservation</a>
			<a href="/live-brands">Live Brands</a>
			<a href="/vat-request" style="cursor: pointer;">VAT Receipt Request</a>
		</nav>

		<button
			class="hamburger-button"
			class:active={isMobileMenuOpen}
			onclick={toggleMenu}
			aria-label="Toggle menu"
		>
			<div class="hamburger-line"></div>
			<div class="hamburger-line"></div>
			<div class="hamburger-line"></div>
		</button>
	</div>
</header>

{#if isMobileMenuOpen}
	<div class="mobile-menu-overlay" transition:fade={{ duration: 200 }}>
		<nav class="mobile-nav">
			<a href="/" onclick={toggleMenu}>Home</a>
			<a href="/menu" onclick={toggleMenu}>Menu</a>
			<a href="/reservation" onclick={toggleMenu}>Reservation</a>
			<a href="/live-brands" onclick={toggleMenu}>Live Brands</a>
			<a href="/vat-request" onclick={toggleMenu}>VAT Receipt Request</a>
		</nav>
	</div>
{/if}

<style>
	header {
		display: flex;
		flex-direction: column;
		justify-content: center;
		width: 100%;
		margin: 3rem 0 1rem;
	}
	.header-logo-section {
		text-align: center;
	}
	.logo-link {
		text-decoration: none;
		color: black;
	}
	.logo-wrapper img {
		width: 120px;
	}
	.logo-wrapper h2 {
		font-size: 1.75rem;
		font-weight: bolder;
		padding-bottom: 5px;
		line-height: 1.35em;
		margin: 0;
	}
	.tagline-wrapper p {
		font-size: 12px;
		margin: 0;
	}
	.header-nav-section {
		margin-top: 1rem;
	}
	hr {
		border: none;
		border-top: 1px solid rgba(0, 0, 0, 0.15);
		margin: 1rem 5rem 0.45rem;
	}

	/* --- Navigation Styles --- */
	.desktop-nav {
		place-self: center;
		display: flex;
		gap: 2rem;
		font-size: 14px;
	}
	.desktop-nav a {
		text-decoration: none;
		color: #191919;
		transition: color 0.2s;
	}
	.desktop-nav a:hover {
		color: #888;
	}

	/* --- Hamburger Menu Styles (ฉบับแอนิเมชัน) --- */
	.hamburger-button {
		display: none;
		background: none;
		border: none;
		cursor: pointer;
		padding: 10px;
		z-index: 101;
		width: 45px;
		height: 32px;
		position: relative;
	}
	.hamburger-line {
		width: 25px;
		height: 2px;
		background-color: #333;
		border-radius: 2px;
		position: absolute;
		left: 10px;
        
		transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
	}
	.hamburger-line:nth-child(1) {
		transform: translateY(-7px);
	}
	.hamburger-line:nth-child(3) {
		transform: translateY(7px);
	}

	/* --- Active State for Animation --- */
	.hamburger-button.active .hamburger-line:nth-child(1) {
		transform: translateY(0) rotate(-45deg);
	}
	.hamburger-button.active .hamburger-line:nth-child(2) {
		opacity: 0;
	}
	.hamburger-button.active .hamburger-line:nth-child(3) {
		transform: translateY(0) rotate(45deg);
	}

	/* --- Mobile Menu Overlay --- */
	.mobile-menu-overlay {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background-color: #f7f2ea;
		z-index: 100;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.mobile-nav {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 2.5rem;
	}
	.mobile-nav a {
		font-size: 1.5rem;
		font-weight: 300;
		color: #333;
		text-decoration: none;
	}

	/* --- Responsive Breakpoint --- */
	@media (max-width: 768px) {
		.desktop-nav {
			display: none;
		}
		.hamburger-button {
			display: block;
			position: fixed;
			right: 24px;
			top: 24px;
			margin: 0;
		}
		hr {
			display: none;
		}
	}
</style>
<!-- <script lang="ts">
	import { fade } from 'svelte/transition';

	// 1. สร้าง State สำหรับควบคุมการเปิด/ปิดเมนูมือถือ
	let isMobileMenuOpen = $state(false);

	function toggleMenu() {
		isMobileMenuOpen = !isMobileMenuOpen;
	}
</script>

<header>
	<div class="header-logo-section">
		<a href="/" class="logo-link">
			<div class="logo-wrapper">
				<img src="/images/logo/tepbar-logo.png" alt="tepbar logo" />
				<h2>TEP BAR</h2>
			</div>
		</a>
		<div class="tagline-wrapper">
			<p>The Cultural Bar of Thailand | Since 2015</p>
		</div>
	</div>

	<div class="header-nav-section">
		<hr />
		<nav class="desktop-nav">
			<a href="/">Home</a>
			<a href="/menu">Menu</a>
			<a href="/reservation" style="cursor: pointer;">Reservation</a>
			<a href="/live-brands">Live Brands</a>
			<a href="/vat-request" style="cursor: pointer;">VAT Receipt Request</a>
		</nav>

		<button
			class="hamburger-button"
			class:hidden={isMobileMenuOpen}
			onclick={toggleMenu}
			aria-label="Open menu"
		>
			<div class="hamburger-line"></div>
			<div class="hamburger-line"></div>
			<div class="hamburger-line"></div>
		</button>
	</div>
</header>

{#if isMobileMenuOpen}
	<div class="mobile-menu-overlay" transition:fade={{ duration: 200 }}>
		<button class="close-button" onclick={toggleMenu} aria-label="Close menu">×</button>
		<nav class="mobile-nav">
			<a href="/" onclick={toggleMenu}>Home</a>
			<a href="/menu" onclick={toggleMenu}>Menu</a>
			<a href="/reservation" onclick={toggleMenu}>Reservation</a>
			<a href="/live-brands" onclick={toggleMenu}>Live Brands</a>
			<a href="/vat-request" onclick={toggleMenu}>VAT Receipt Request</a>
		</nav>
	</div>
{/if}

<style>
	header {
		display: flex;
		flex-direction: column;
		justify-content: center;
		width: 100%;
		margin: 3rem 0 1rem;
	}
	.header-logo-section {
		text-align: center;
	}
	.logo-link {
		text-decoration: none;
		color: black;
	}
	.logo-wrapper img {
		width: 120px;
	}
	.logo-wrapper h2 {
		font-size: 1.75rem;
		font-weight: bolder;
		padding-bottom: 5px;
		line-height: 1.35em;
		margin: 0;
	}
	.tagline-wrapper p {
		font-size: 12px;
		margin: 0;
	}
	.header-nav-section {
		margin-top: 1rem;
	}
	hr {
		border: none;
		border-top: 1px solid rgba(0, 0, 0, 0.15);
		margin: 1rem 5rem 0.45rem;
	}

	/* --- Navigation Styles --- */
	.desktop-nav {
		place-self: center;
		display: flex;
		gap: 2rem;
		font-size: 14px;
	}
	.desktop-nav a {
		text-decoration: none;
		color: #191919;
		transition: color 0.2s;
	}
	.desktop-nav a:hover {
		color: #888;
	}

	/* --- Hamburger Menu Styles --- */
	.hamburger-button {
		display: none;
		background: none;
		border: none;
		cursor: pointer;
		padding: 10px;
		z-index: 101; /* ทำให้ปุ่มอยู่เหนือเนื้อหาอื่น */
	}
	.hamburger-line {
		width: 25px;
		height: 2px;
		background-color: #333;
		margin: 5px 0;
	}

	/* 2. เพิ่ม Style สำหรับซ่อนปุ่ม */
	.hamburger-button.hidden {
		display: none;
	}

	/* --- Mobile Menu Overlay --- */
	.mobile-menu-overlay {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background-color: #f7f2ea;
		z-index: 100;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.close-button {
		position: absolute;
		top: 2rem;
		right: 2rem;
		background: none;
		border: none;
		font-size: 2.5rem;
		cursor: pointer;
		color: #333;
		z-index: 101; /* ทำให้ปุ่มปิดอยู่เหนือ Overlay */
	}
	.mobile-nav {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 2.5rem;
	}
	.mobile-nav a {
		font-size: 1.5rem;
		font-weight: 300;
		color: #333;
		text-decoration: none;
	}

	/* --- Responsive Breakpoint --- */
	@media (max-width: 768px) {
		.desktop-nav {
			display: none;
		}
		.hamburger-button {
			display: block;
			position: fixed;
			right: 24px;
			top: 24px;
			margin: 0; /* Override margin เดิม */
		}
		hr {
			display: none;
		}
	}
</style> -->