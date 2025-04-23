<script>
    import { onMount } from "svelte";
    import Alpaca from "$lib/images/alpaca.png";
    import { dev } from "$app/environment";
    import { injectAnalytics } from '@vercel/analytics/sveltekit'
    import { page } from '$app/stores';

    injectAnalytics({mode: dev ? 'development' : 'production'});

    let showMobileMenu = false;

    const navItems = [
        {label: "", href: "/", isLogo: true},
        {label: "Home", href: "/"},
        {label: "Projects", href:"/projects"},
        {label: "Forløb", href: "/forloeb"}
    ];

    const handleMobileClick = () => {
        showMobileMenu = !showMobileMenu;
    };


    const handleNavClick = () => {
        if (window.innerWidth <= 768) {
            showMobileMenu = false;
        }
    };



    /**
     * @param {MediaQueryListEvent} e
     */
    const mediaQueryHandler = (e) =>{
        if(!e.matches){
            showMobileMenu = false;
        }
    };

    /**
     * @param {Event} event
     */
    const handleKeyPress = (event) => {
        if (event instanceof KeyboardEvent && event.key === "Enter") {
            handleMobileClick();
        }
    };

</script>

<nav>
    <div class="inner">
        <div 
            class="mobile-icon {showMobileMenu ? 'active' : ''}" 
            role="button"
            tabindex="0"
            aria-label="Toggle mobile menu"
            on:click={handleMobileClick}
            on:keydown={handleKeyPress}
        >
            <div class="middle-line"></div>
        </div>
        <ul class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>
            {#each navItems as item, index}
                <li>
                    {#if item.isLogo}
                        <a class="image-alpaca" href={item.href}>
                            <img class="logo-image" src={Alpaca} alt="Alpaca Logo" />
                        </a>
                    {:else}
                        <a 
                            class="listNav" 
                            class:active={$page.url.pathname === item.href}
                            href={item.href}
                            on:click={handleNavClick}
                        >
                            {item.label}
                        </a>
                    {/if}
                </li>
            {/each}
        </ul>
    </div>
</nav>

<slot />

<style>
    :global(body) {
        font-family: 'Inter', system-ui, -apple-system, sans-serif;
        background-color: #fafafa;
        color: #1a1a1a;
        line-height: 1.6;
        min-height: 100vh;
        margin: 0;
    }

    nav {
        background: rgba(255, 255, 255, 0.8);
        backdrop-filter: blur(10px);
        height: 72px;
        position: sticky;
        top: 0;
        z-index: 1000;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
        border-bottom: 1px solid rgba(255, 255, 255, 0.3);
    }

    .inner {
        max-width: 1280px;
        margin: 0 auto;
        padding: 0 32px;
        height: 100%;
        display: flex;
        align-items: center;
    }


    .logo-image {
        height: 48px;
        transition: transform 0.3s ease;
        user-select: none;
    }

    .logo-image:hover {
        transform: scale(1.05);
    }

    .mobile-icon {
        display: none;
        width: 32px;
        height: 31px;
        position: relative;
        cursor: pointer;
        background: transparent;
        border: none;
        padding: 0;
    }

    .navbar-list {
        display: flex;
        align-items: center;
        gap: 2rem;
        margin: 0;
        padding: 0;
        list-style: none;
    }

    .navbar-list a:not(.image-alpaca) {
        color: #1a1a1a;
        text-decoration: none;
        padding: 8px 16px;
        border-radius: 8px;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        font-weight: 500;
        position: relative;
        background: rgba(138, 43, 226, 0.01);
    }

    .navbar-list a:not(.image-alpaca):hover {
        background: rgba(138, 43, 226, 0.1);
        color: blueviolet;
    }

    .navbar-list a:not(.image-alpaca)::after {
        content: '';
        position: absolute;
        bottom: -4px;
        left: 50%;
        width: 0;
        height: 2px;
        background: blueviolet;
        transition: width 0.3s ease, left 0.3s ease;
    }

    .navbar-list a:not(.image-alpaca):hover::after {
        width: 100%;
        left: 0;
    }

    @media (max-width: 480px) {
        .inner {
            padding: 0 16px;
            justify-content: space-between; 
        }

        .mobile-icon {
            display: block;
            margin-left: auto;
            z-index: 2; 
        }

        .navbar-list {
            display: none;
            position: fixed;
            top: 72px;
            left: 0;
            right: 0;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            flex-direction: column;
            padding: 16px;
            gap: 1rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border-radius: 0 0 16px 16px;
            z-index: 1000; 
        }

        .logo-image {
            height: 40px;
            margin-right: 0; 
            display: block; 
        }

        .image-alpaca {
            display: block;
            margin-bottom: 1rem;
        }

        .navbar-list.mobile {
            display: flex !important;
        }
    }

    @media (min-width: 481px) and (max-width: 768px) {
        .inner {
            padding: 0 24px;
        }

        .mobile-icon {
            display: block;
            margin-left: auto;
        }

        .navbar-list {
            display: none;
            position: fixed;
            top: 72px;
            left: 0;
            right: 0;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            flex-direction: column;
            padding: 24px;
            gap: 1.5rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border-radius: 0 0 16px 16px;
        }
    }

    @media (max-width: 768px) {
        .navbar-list.mobile {
            display: flex;
        }

        .navbar-list a:not(.image-alpaca) {
            width: 100%;
            justify-content: center;
            padding: 12px 24px;
        }
    }

    @media(min-width: 769px){
        .image-alpaca{
            margin-right: 3rem;
        }
    }

    .mobile-icon:after,
    .mobile-icon:before,
    .middle-line {
        content: "";
        position: absolute;
        left: 0;
        width: 100%;
        height: 2px;
        background: #1a1a1a;
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .mobile-icon:before {
        top: 6px;
    }

    .mobile-icon:after {
        bottom: 6px;
    }

    .middle-line {
        top: 50%;
        transform: translateY(-50%);
        opacity: 1;
    }

    .mobile-icon.active:before {
        transform: rotate(45deg) translateY(8px);
    }

    .mobile-icon.active:after {
        transform: rotate(-45deg) translateY(-8px);
    }

    .mobile-icon.active .middle-line {
        opacity: 0;
        transform: translateX(-20px);
    }

    .navbar-list a:not(.image-alpaca).active {
        background: rgba(138, 43, 226, 0.1);
        /* color: blueviolet; */
    }


</style>