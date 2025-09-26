<!-- <h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p> -->
<!-- <main>
    <div>
        <img src="/images/banner/homepage.png" alt="" style="object-fit: cover; max-width: 100%;">
        <div style="place-self: center; text-align: center;">
            <h2 style="font-size: 2rem; padding: 1rem; font-weight: 300;">WELCOME TO TEP BAR</h2>
            <p>The Cultural Bar | Since 2015</p>
        </div>
    </div>
</main> -->

<svelte:head>
    <title>[Clone] Home | TEP BAR</title>
</svelte:head>

<main>
    <div class="banner-container">
        <img src="/images/banner/homepage.png" alt="บรรยากาศภายในร้านเทพ บาร์" class="banner-image">

        <div class="banner-text">
            <h2 style="font-size: 2.5rem; padding: 1rem; font-weight: 300;">WELCOME TO TEP BAR</h2>
            <p>The Cultural Bar | Since 2015</p>
        </div>
    </div>
</main>

<style>
    .banner-container {
        position: relative; /* สร้างขอบเขตให้ element ลูกที่ "position: absolute" มาอ้างอิง */
        width: 100%;
        color: white; /* เปลี่ยนสีตัวอักษรเป็นสีขาวเพื่อให้มองเห็นชัดบนภาพ */
    }

    .banner-image {
        display: block; /* แก้ปัญหาช่องว่างเล็กๆ ใต้ภาพ */
        width: 100%;
        height: auto;
        /* อาจจะเพิ่มความสว่างหรือฟิลเตอร์ให้ข้อความเด่นขึ้น */
        filter: brightness(0.7);
        height: 70%;
    }

    .banner-text {
        position: absolute; /* ทำให้ element นี้ลอยขึ้นมา */
        
        /* เทคนิคการจัดกลางสมบูรณ์แบบ */
        top: 40%;
        left: 50%;
        transform: translate(-50%, -50%);

        /* จัดสไตล์ข้อความเพิ่มเติม */
        width: 100%; /* ทำให้ข้อความไม่ตกขอบจอเล็ก */
        text-align: center;
        padding: 1rem;
    }
</style>