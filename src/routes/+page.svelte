<script>
    import { onMount } from 'svelte';

    let age = 0;

    function calculateAge() {
        const birthYear = 1988;
        const birthMonth = 7; 
        const birthDay = 19;
        
        const today = new Date();
        let currentAge = today.getFullYear() - birthYear;
        
        if (today.getMonth() < birthMonth || 
            (today.getMonth() === birthMonth && 
             today.getDate() < birthDay)) {
            currentAge--;
        }
        return currentAge;
    }

    onMount(() => {
        age = calculateAge();
    });
</script>

<svelte:head>
    <title>Home</title>
</svelte:head>

<style>
    .mainName {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 2rem 1rem; 
        text-align: center; 
    }
    .mainName h1 {
        margin: 0;
        font-size: 2rem;
        line-height: 1.2;
        max-width: 100%;
        position: relative;
    }

    @media (max-width: 380px) {
        .mainName h1 {
            font-size: 1.75rem;
        }
    }

    .aboutme {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 85%;
        margin: 0 auto;
        font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
        font-size: 20px;
        text-align: center;
        line-height: 1.5;
    }

    .mainName h1::after {
        content: '';
        width: 60px;
        height: 4px;
        background: rgba(138, 43, 226, 0.6);
        position: absolute;
        bottom: -1rem;
        left: 50%;
        transform: translateX(-50%);
        border-radius: 2px;
    }
</style>

<div class="welcome-text">
    <div class="mainName">
        <h1>Welcome to Stefan's portfolio</h1>
    </div>
    <div class="aboutme">
        <p>
            I'm a <span>{age}</span> year old guy who decided to switch day jobs for books during a pandemic. I started learning C# and have a couple of projects on GitHub. More projects will be added as I complete them. I also dabble in Zig and Unity. This website was made with SvelteKit.
        </p>
    </div>
</div>