<script lang="ts">
	// --- Type Definition ---
	type Band = {
		image: string;
		name: string;
		description: string;
		schedule: string;
	};

	// --- Band Data ---
	const bands: Band[] = [
		{
			image: '/images/live-brands/1-Krungthep Ratri.png',
			name: 'Krungthep Ratri',
			description:
				'A Thai Retro City-Pop band that tells stories of Bangkok life from the past to the present through music. Enjoy classic Luk Krung and popular Thai pop hits from the 80s. The band features keyboard, guitar, cajón, violin, and a lead vocalist.',
			schedule: 'Live: every Monday 💛'
		},
		{
			image: '/images/live-brands/2-Khamvisedth.png',
			name: 'Khamvisedth',
			description:
				'Offers a fresh take on Esan music with a modern urban twist, blending traditional Isan melodies with contemporary sounds. The band’s unique style is brought to life with phin, khaen, pi chum, Thai drums, and a lead vocalist.',
			schedule: 'Live: every Tuesday 🩷'
		},
		{
			image: '/images/live-brands/3-Thursday Band.png',
			name: 'Thursday Band',
			description:
				'(aka Wan Pruhat) is a classic string band performing luk thung, luk krung, and lively folk dance tunes. Experience vintage Thai music in a modern setting, with khim, saw, Thai drums, and a lead vocalist.',
			schedule: 'Live: every Wednesday, Saturday 💚💜'
		},
		{
			image: '/images/live-brands/4-Samniang Tep.png',
			name: 'Samniang Tep',
			description:
				'A unique piphat ensemble led by Thai xylophone sounds, featuring vibrant traditional sounds and rhythms such as ram wong and long drum. The band includes ranad ek, saw u, flute, drums, and a lead vocalist.',
			schedule: 'Live: every Thursday, Sunday 🧡❤️'
		},
		{
			image: '/images/live-brands/5-Sam Saw.png',
			name: 'Sam Saw',
			description:
				'A traditional Thai string trio rarely heard today, blending rural and cultural folk music from all four regions of Thailand. The ensemble includes saw sam sai, saw u, saw duang, a traditional pump organ, and a lead vocalist.',
			schedule: 'Live: every Friday 🩵'
		},
		{
			image: '/images/live-brands/6-TEP Music Room.png',
			name: 'TEP Music Room',
			description: 'A special event celebrating our 9th anniversary on Nov 23, and Nov 24, 2024',
			schedule: '' // No regular schedule
		}
	];
</script>

<svelte:head>
    <title>[Clone] Live Brands | TEP BAR</title>
</svelte:head>

<main>
    <section>
        <h1 class="livebrands-h1">Traditional Thai Music Experience at TEP BAR</h1>
        <a class="schedules-link" href="https://docs.google.com/spreadsheets/d/1enhGqS83lMKS0YqOF1N6Y8UOqAL4jvMxtTXqfTyPIfY/edit?gid=296304222#gid=296304222">
            <p class="schedules">
                Live Schedules!
            </p>
        </a>
        <div style="width: 31px; place-self: center; height: 3px; background-color: #000; border-radius: 1rem; margin: 1rem 1rem 2rem ;"></div>
    </section>
    <section>
        <img style="width: 100%; object-fit: cover;" src="/images/banner/tepbar-_livebrands_banner.png" alt="">
        <div class="livebrands-description">
            <p>is at the heart of our mission to honor and elevate Thai culture in every possible way. From the ingredients in our cocktails to our decor and architecture, we celebrate the roots of Thai heritage, weaving its essence into an experience that’s vibrant, authentic, and modern. Since opening in 2015, we’ve aimed to revive and reimagine traditional Thai music—breathing new life into sounds that echo Thailand's cultural richness. Starting with just one band on day one, TEP BAR has since become the birthplace of five unique bands. Each is carefully assembled to embody and reinterpret Thai musical traditions in their own way. Performing on rotation, these ensembles are more than just entertainers; they are storytellers, transporting our guests to the essence of Thai heritage with every note. It’s our pride and privilege to help this music soar, evolving and resonating with new generations while rooted in tradition. At TEP BAR, we’re not just preserving Thai music; we’re creating a space where it lives, thrives, and inspires far into the future.</p>
            <br>
            <p> you’re not just here for a drink but for a full cultural immersion. Our live music performances are a gateway to Thailand’s musical legacy, showcasing traditional instruments like the Ranad Ek (Thai xylophone), Khim, Saw U, Pi Chum, and many more. These instruments create a rich, multi-layered soundscape that transports listeners to another world—a uniquely Thai experience only here at TEP BAR.</p>
        </div>
    </section>
    <section style="margin-top: 3rem;">
        <h2 style="font-size: 38px; font-weight: 400; place-self: center;">Meet The Bands</h2>
        <div style="width: 31px; place-self: center; height: 3px; background-color: #000; border-radius: 1rem; margin: 1rem 1rem 2rem ;"></div>
        <div class="bands-container">
            {#each bands as band}
                <div class="band-card">
                    <img src={band.image} alt={band.name} />
                    <div class="band-info">
                        <p><b style="font-size: 15px;">{band.name}</b></p>
                        <p style="font-size: 12px;">{band.description}</p>
                        <br />
                        {#if band.schedule}
                            <p style="font-size: 13px;">{band.schedule}</p>
                        {/if}
                    </div>
                </div>
            {/each}
        </div>
    </section>
</main>


<style>
    main {
        margin-bottom: 2rem;
    }

    .livebrands-h1 {
        font-size: 40px; 
        place-self: center;
    }

    .schedules-link {
        text-decoration: none;
    }
    .schedules-link:hover {
        text-decoration: underline;
    }

    .schedules {
        place-self: center; color: #221F7B; font-size: 16px; letter-spacing: 0.15em; font-weight: 700; 
        /* --- เพิ่มบรรทัดนี้เพื่อเรียกใช้ animation --- */
        animation: blinking-fade 2s infinite;
    }

	/* 1. กำหนด Keyframes ของแอนิเมชัน */
	@keyframes blinking-fade {
		0% {
			opacity: 1; /* เริ่มต้น: มองเห็นชัดสุด */
		}
		50% {
			opacity: 0; /* กึ่งกลาง: หายไป */
		}
		100% {
			opacity: 1; /* กลับมามองเห็นชัดสุดอีกครั้ง */
		}
	}

    /* /-------------------------- */
    .livebrands-description {
        margin: 2px;
        font-size: 12px;
    }

        /* ... style อื่นๆ ของคุณ ... */

    .bands-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr); /* 👈 Default: 3 คอลัมน์ */
        gap: 2rem; /* ช่องว่างระหว่างการ์ด */
        padding: 0 2rem; /* เพิ่ม padding ด้านข้าง */
    }

    .band-card {
        display: flex;
        flex-direction: column;
        /* gap: 1rem; */
    }

    .band-card img {
        width: 100%;
        height: auto;
        aspect-ratio: 1 / 1; /* ทำให้รูปเป็นสี่เหลี่ยมจัตุรัส */
        object-fit: cover;
    }

    .band-info {
        text-align: left;
        padding: 0.5rem;
    }

    /* --- Responsive Breakpoint --- */
    @media (max-width: 1024px) {
        .bands-container {
            grid-template-columns: repeat(2, 1fr); /* 👈 จอเล็กกว่า 1024px: 2 คอลัมน์ */
        }
    }

    @media (max-width: 768px) {
        .livebrands-h1 {
            font-size: 19px; 
            text-align: center;
            width: 250px;
            line-height: 1rem;
            margin-bottom: 2rem;
        }
    }

    @media (max-width: 640px) {
        .bands-container {
            grid-template-columns: 1fr; /* 👈 จอมือถือ: 1 คอลัมน์ */
        }
    }
</style>