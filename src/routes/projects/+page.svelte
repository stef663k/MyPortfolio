<script>
    import calculator from "$lib/images/calculator.png";
    import server from "$lib/images/server.png";
    import scraper from "$lib/images/scraper.png";
    import svelteImage from "$lib/images/svelte.png";
    import zig from "$lib/images/zig.png";
    import maui from "$lib/images/dotnet-removebg-preview.png";
</script>
<title>Projects</title>
<style>
    :global(body) {
        background: #f8f9fa;
        font-family: 'Inter', system-ui, -apple-system, sans-serif;
        margin: 0;
        color: #2d3436;
    }
        .projectBack {
            display: flex;
            justify-content: center;
            padding: 4rem 0 3rem;
            background: linear-gradient(135deg, #4d0b8a 0%, #8a2be2 50%, #60219a 100%);
            color: white;
            margin: 0;
            position: relative;
            overflow: hidden;
        }

        .projectBack::before {
            content: '';
            position: absolute;
            width: 150%;
            height: 150%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, rgba(0,0,0,0.1) 100%);
            pointer-events: none;
        }

        .projectBack h1 {
            font-size: 2.75rem;
            margin: 0;
            font-weight: 700;
            letter-spacing: -0.5px;
            position: relative;
            z-index: 1;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }

    .project-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        box-sizing: border-box;
        max-width: 1080px;
        margin: -2.5rem auto 3rem;
    }

    .project-card {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        box-sizing: border-box;
        border-radius: 24px;
        padding: 2.5rem;
        box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        border: 1px solid rgba(255, 255, 255, 0.3);
        position: relative;
}



    .project-card h3 {
        font-size: 1.25rem;
        color: #0f172a;
        margin-bottom: 1.5rem;
        padding-bottom: 0.5rem;
        border-bottom: 2px solid #e2e8f0;
    }

    .project-list {
        display: grid;
        gap: 1.5rem;
        padding: 0;
        list-style: none;
        margin: 0;
    }

    .project-item {
        display: flex;
        align-items: center;
        gap: 1.5rem;
        padding: 1rem;
        border-radius: 12px;
        transition: background 0.3s ease;
        box-sizing: border-box;
    }

    .project-item:hover {
        background: rgba(241, 245, 249, 0.5);
    }

    .project-image {
        width: 80px;
        height: 80px;
        border-radius: 12px;
        object-fit: contain;
        padding: 12px;
        background: rgba(138, 43, 226, 0.1);
        transition: transform 0.3s ease;
    }

    .project-item:hover .project-image {
        transform: scale(1.05);
    }

    .project-info {
        flex-grow: 1;
    }

    .project-link {
        color: #0f172a;
        font-weight: 600;
        text-decoration: none;
        display: block;
        margin-top: 0.25rem;
        position: relative;
    }

    .project-link::after {
        content: '';
        position: absolute;
        bottom: -2px;
        left: 0;
        width: 0;
        height: 2px;
        background: blueviolet;
        transition: width 0.3s ease;
    }

    .project-link:hover::after {
        width: 100%;
    }

    .project-description {
        color: #64748b;
        font-size: 0.9rem;
        margin-top: 0.5rem;
    }
            @media (max-width: 480px){
            .projectBack h1 {
                font-size: 1.5rem;
                padding: 0.1rem;
                text-align: center;
            }

            .project-grid {
                margin: -2rem auto 2rem;
            }
            .project-card {
                padding: 1rem;
            }
        }

        @media (max-width: 768px) {
            .projectBack h1 {
                font-size: 2rem;
                padding: 0 1rem;
                text-align: center;
            }

            .project-grid {
                margin: -2rem auto 2rem;
        
            }
            .project-card {
                padding: 1.5rem;
                border-radius: 16px;
            }

        }
        @media (min-width: 769px) {
            .project-card:hover {
                transform: translateY(-5px);
                box-shadow: 0 12px 40px rgba(0,0,0,0.1);
            }
        }

</style>

<div class="projectName">
    <div class="projectBack">
        <h1>Projects</h1>
    </div>
    
    <div class="project-grid">
        <div class="project-card">
            <h3>GitHub Projects</h3>
            <ul class="project-list">
                <li class="project-item">
                    <a href="https://github.com/stef663k/WebServer" class="project-link">
                        <img src={server} alt="Web Server" class="project-image" />
                        <div class="project-info">
                            <span>Web Server</span>
                            <div class="project-description">Custom web server implementation with advanced routing</div>
                        </div>
                    </a>
                </li>
                <li class="project-item">
                    <a href="https://github.com/stef663k/ZigConsoleCalculator" class="project-link">
                        <img src={calculator} alt="Calculator" class="project-image" />
                        <div class="project-info">
                            <span>Zig Console Calculator</span>
                            <div class="project-description">Terminal-based calculator built with Zig</div>
                        </div>
                    </a>
                </li>
                <li class="project-item">
                    <a href="https://github.com/stef663k/Webscraper" class="project-link">
                        <img src={scraper} alt="Web Scraper" class="project-image" />
                        <div class="project-info">
                            <span>Web Scraper</span>
                            <div class="project-description">Data extraction tool for web content analysis</div>
                        </div>
                    </a>
                </li>
            </ul>
        </div>
    </div>
</div>

