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
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com">

    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400&display=swap" rel="stylesheet">
    <title>[Clone] Home | TEP BAR</title>
    <meta name="description" content="Experience the essence of Thai culture through music, cocktails, and ambiance. TEP BAR(เทพบาร์) — Thailand's only Cultural Bar, established in 2015." />
</svelte:head>

<main>
    <div class="banner-container">
        <img src="/images/banner/homepage.avif" alt="บรรยากาศภายในร้านเทพ บาร์" class="banner-image" fetchpriority=high width="1800" height="1200">
        <!-- <img
            src="/images/banner/homepage-1200w.avif"
            srcset="/images/banner/homepage-480w.avif 480w,
                    /images/banner/homepage-800w.avif 800w,
                    /images/banner/homepage-1200w.avif 1200w,
                    /images/banner/homepage-1800w.avif 1800w"
            sizes="100vw"
            alt="บรรยากาศภายในร้านเทพ บาร์"
            class="banner-image"
            fetchpriority="high"
            width="1800"
            height="1850"
        /> -->

        <div class="banner-text">
            <h2 style="font-size: 2.5rem; padding: 1rem 0; font-weight: 300;">WELCOME TO TEP BAR</h2>
            <p>The Cultural Bar | Since 2015</p>
        </div>
    </div>
</main>

<style>
    /* 1. สร้างฟอนต์สำรองชื่อ 'Sarabun Fallback' โดยใช้ฟอนต์ Arial ที่มีในเครื่อง */
    @font-face {
        font-family: 'Sarabun Fallback';
        src: local('Arial'); /* หรือฟอนต์พื้นฐานอื่นๆ */
        /* ค่าเหล่านี้ต้องคำนวณมาเพื่อให้พอดีกับฟอนต์ Sarabun */
    }

    /* 2. ใน CSS ของ banner-text ให้อ้างอิงถึงฟอนต์สำรองนี้ */
    .banner-text {
        /* ให้ Browser ลองใช้ Sarabun ก่อน, ถ้ายังไม่มีให้ใช้ Sarabun Fallback ที่เราสร้าง, ถ้าไม่มีอีกก็ใช้ sans-serif ทั่วไป */
        font-family: 'Sarabun', 'Sarabun Fallback', sans-serif;
    }

    h2 {
        font-family: 'Sarabun', 'Sarabun Fallback', sans-serif;
    }


    .banner-container {
        position: relative; /* สร้างขอบเขตให้ element ลูกที่ "position: absolute" มาอ้างอิง */
        width: 100%;
        color: white; /* เปลี่ยนสีตัวอักษรเป็นสีขาวเพื่อให้มองเห็นชัดบนภาพ */
    }

    .banner-image {
        display: block; /* แก้ปัญหาช่องว่างเล็กๆ ใต้ภาพ */
        place-self: center;
        width: 99%;
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
    }

    @media (max-width: 768px) {
        .banner-image {
            width: 100%;
        }
    }
</style>