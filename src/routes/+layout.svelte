<script>
    import { onMount } from "svelte";
    import Alpaca from "$lib/images/alpaca.png";

    let showMobileMenu = false;

    const navItems = [
        {label: "", href: "/", isLogo: true},
        {label: "Home", href: "/"},
        {label: "Projects", href:"/Projects"},
        {label: "Forløb", href: "/Forløb"}
    ];

    const handleMobileClick = () => (showMobileMenu = !showMobileMenu);

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

    onMount(() => {
        const mediaListener = window.matchMedia("(max-width: 767px)");

        mediaListener.addEventListener("change", mediaQueryHandler);

        const mobileIcon = document.querySelector(".mobile-icon");

            /**
            * @type {HTMLDivElement}
            */
        if (mobileIcon) {
            mobileIcon.addEventListener("click", handleMobileClick);
            mobileIcon.addEventListener("keydown", handleKeyPress);
        }
  });


</script>

<nav>
    <div class="inner">
        <!-- Mobile toggle button remains the same -->
        <ul class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>
            {#each navItems as item, index}
                <li>
                    {#if item.isLogo}
                        <a class="image-alpaca" href={item.href}>
                            <img class="logo-image" src={Alpaca} alt="Alpaca Logo" />
                        </a>
                    {:else}
                        <a class="listNav" href={item.href}>{item.label}</a>
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
        margin-right: 3rem;
        transition: transform 0.3s ease;
    }

    .logo-image:hover {
        transform: scale(1.05);
    }

    /* Modern mobile menu icon */
    .mobile-icon {
        display: none;
        width: 32px;
        height: 32px;
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

    /* Modern mobile menu */
    @media (max-width: 767px) {
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

        .navbar-list.mobile {
            display: flex;
        }

        .navbar-list a:not(.image-alpaca) {
            width: 100%;
            justify-content: center;
            padding: 12px 24px;
            background: rgba(138, 43, 226, 0.05);
        }
    }

    /* Modern hamburger animation */
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
</style>