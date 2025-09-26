<!-- SvelteKit(Svelte5): $lib/components/go/MenuDropdown.svelte -->
<script lang="ts">
    // 🦖1. Import 'browser' เข้ามา
    import { browser } from '$app/environment';
    import { onMount, onDestroy } from 'svelte';

    // --- Type Definition ---
    type MenuCategory = {
        value: string;
        thai: string;
        english: string;
    };

    // --- Props ---
    // ลบ initialValue ออก, ทำให้ selectedValue เป็น bindable prop
    let {
        items,
        selectedValue = $bindable(items[0]?.value ?? '')
    }: {
        items: MenuCategory[];
        selectedValue?: string;
    } = $props();

    // --- State using Runes ---
    let isOpen = $state(false);
    // บรรทัดนี้จะทำงานได้อย่างถูกต้องเมื่อ selectedValue ถูก bind ค่ามาจากข้างนอก
    let selectedItem = $derived(items.find((item) => item.value === selectedValue) ?? items[0]);
    let dropdownElement: HTMLElement | null = $state(null);

    // --- Functions (เหมือนเดิม) ---
    function toggleDropdown() {
        isOpen = !isOpen;
    }

    function selectOption(value: string) {
        selectedValue = value;
        isOpen = false;
    }

    function handleClickOutside(event: MouseEvent) {
        if (dropdownElement && !dropdownElement.contains(event.target as Node)) {
            isOpen = false;
        }
    }

    // --- Lifecycle ---
	onMount(() => {
        // 🦖2. เพิ่มเงื่อนไขเช็คว่าโค้ดรันบน browser หรือไม่
		if (browser) {
			document.addEventListener('click', handleClickOutside, true);
		}
	});

	onDestroy(() => {
        // 🦖3. เพิ่มเงื่อนไขที่นี่ด้วย
		if (browser) {
			document.removeEventListener('click', handleClickOutside, true);
		}
	});
</script>

<div class="custom-select-container" bind:this={dropdownElement}>
	<button class="select-selected" onclick={toggleDropdown} aria-haspopup="listbox" aria-expanded={isOpen}>
		<span>
			{items.findIndex((item) => item.value === selectedItem.value) + 1}) {selectedItem.thai}
			{#if selectedItem.english}
				| {selectedItem.english}
			{/if}
		</span>
		<span class="arrow" class:open={isOpen}></span>
	</button>

	{#if isOpen}
		<div class="select-items" role="listbox">
			{#each items as item, i}
				<div
					class="select-option"
					class:selected={item.value === selectedValue}
					onclick={() => selectOption(item.value)}
					role="option"
					aria-selected={item.value === selectedValue}
					tabindex="0"
					onkeydown={(e) => {
						if (e.key === 'Enter' || e.key === ' ') selectOption(item.value);
					}}
				>
					{i + 1}) {item.thai}
					{#if item.english}
						| {item.english}
					{/if}
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.custom-select-container {
		position: relative;
		width: 320px;
		font-size: 1rem;
		user-select: none;
	}

	.select-selected {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		background-color: #fff;
		border: 1px solid #333;
		padding: 1rem;
		cursor: pointer;
		text-align: left;
        font-size: 1rem;
	}

	.arrow {
		width: 0;
		height: 0;
		border-left: 5px solid transparent;
		border-right: 5px solid transparent;
		border-top: 5px solid #333;
		transition: transform 0.2s ease-in-out;
	}
	.arrow.open {
		transform: rotate(180deg);
	}

	.select-items {
		position: absolute;
		background-color: #fff;
		top: 100%;
		left: 0;
		right: 0;
		border: 1px solid #333;
		border-top: none;
		max-height: 250px;
		overflow-y: auto;
		z-index: 99;
	}

	.select-option {
		padding: 1rem;
		cursor: pointer;
		border-bottom: 1px solid #f0f0f0;
	}
	.select-option:last-child {
		border-bottom: none;
	}

	.select-option:hover {
		background-color: #f1f1f1;
	}

	.select-option.selected {
		background-color: #e0e0e0;
		font-weight: bold;
	}
</style>