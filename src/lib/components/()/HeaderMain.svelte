<!-- SvelteKit(Svelte5): $lib/components/()/HeaderMain.svelte -->
<header>
    <div class="header-section1">
        <a href="/" style="text-decoration: none;">
            <div style="place-self: center; text-align: center;">
                <img src="../images/logo/tepbar-logo.png" alt="tepbar logo" width="50%">
                <h2 style="font-size: 1.75rem; font-weight: bolder; text-decoration: none; color: #000; padding-bottom: 5px; line-height: 1.35em;">TEP BAR</h2>
            </div>
        </a>
        <div style="place-self: center; text-align: center;">
            <p style="font-size: 10px;">The Cultural Bar of Thailand | Since 2015</p>
        </div>
    </div>
    <div class="header-section2">
        <hr style="margin: 1rem 5rem 0.45rem;">
        <div class="navbar">
            <a href="/">
                <div>Home</div>
            </a>
            <a href="/menu">
                <div>Menu</div>
            </a>
            <div style="cursor: pointer;">Reservation</div>
            <a href="/live-brands">
                <div>Live Brands</div>
            </a>
            <div style="cursor: pointer;">VAT Receipt Request</div>
        </div>
    </div>
</header>

<style>
    header {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 100%;
        margin: 3rem 0 1rem;
    }

    .navbar {
        place-self: center;
        display: flex;
        gap: 1rem;
    }
    
    .navbar a{
        text-decoration: none;
        color: #191919;
    }
    .navbar a:hover {
        color: #333;
    }

    .navbar a div, .navbar div  {
        font-size: 14px;
    }
</style>