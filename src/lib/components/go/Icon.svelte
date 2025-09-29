<script lang="ts">
	let { iconData, tooltipText }: { iconData: string; tooltipText: string } = $props();
</script>

<div class="icon-container">
	<div class="icon-wrapper">
		{@html iconData}
	</div>
	<div class="tooltip">{tooltipText}</div>
</div>

<style>
	.icon-container {
		position: relative;
		display: inline-block;
	}

	.icon-wrapper {
		border: 1px solid #ccc;
		border-radius: 999px; /* ทำให้เป็นวงกลม */
		padding: 0 6px;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 32px;
		/* height: 32px; */
		cursor: pointer;
	}

	.icon-wrapper :global(svg) {
		width: 18px;
		height: 18px;
		fill: #555; /* สีของไอคอน */
	}

	/* Tooltip styles */
	.tooltip {
		/* visibility: hidden; */
		width: max-content;
		background-color: #333;
		color: #fff;
		text-align: center;
		border-radius: 6px;
		padding: 5px 10px;
		position: absolute;
		/* z-index: 1; */
		bottom: 125%; /* ตำแหน่ง tooltip ให้อยู่เหนือไอคอน */
		left: 50%;
        transform: translateX(-50%); /* ขยับกลับมาทางซ้าย 50% ของความกว้างตัวเอง */
		/* margin-left: -35px; /* ปรับให้ tooltip อยู่กลางไอคอน */
		opacity: 0; /* ซ่อนไว้ */
        visibility: hidden; /* ซ่อนจากการมองเห็นและการคลิก */
        transition: opacity 0.2s ease, visibility 0.2s ease; /* เพิ่มอนิเมชั่น */
        z-index: 10;
	}

	/* ลูกศรชี้ลงของ tooltip */
	.tooltip::after {
		content: '';
		position: absolute;
		top: 100%;
		left: 50%;
		margin-left: -5px;
		border-width: 5px;
		border-style: solid;
		border-color: #333 transparent transparent transparent;
	}

	/* แสดง tooltip เมื่อ hover */
	.icon-container:hover .tooltip {
		visibility: visible;
		opacity: 1;
	}
</style>