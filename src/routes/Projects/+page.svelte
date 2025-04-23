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

    .projectName {
        max-width: 1280px;
        margin: 0 auto;
        padding: 4rem 2rem;
    }

    h1 {
        font-size: 2.5rem;
        text-align: center;
        margin-bottom: 3rem;
        color: #0f172a;
        position: relative;
    }

    h1::after {
        content: '';
        width: 60px;
        height: 4px;
        background: #3498db;
        position: absolute;
        bottom: -1rem;
        left: 50%;
        transform: translateX(-50%);
        border-radius: 2px;
    }

    .project-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 2rem;
        margin-top: 3rem;
    }

    .project-card {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        border-radius: 16px;
        padding: 2rem;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        box-shadow: 0 8px 32px rgba(0,0,0,0.05);
        border: 1px solid rgba(255, 255, 255, 0.3);
    }

    .project-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 12px 40px rgba(0,0,0,0.1);
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
    }

    .project-item {
        display: flex;
        align-items: center;
        gap: 1rem;
        padding: 1rem;
        border-radius: 12px;
        transition: background 0.3s ease;
    }

    .project-item:hover {
        background: rgba(241, 245, 249, 0.5);
    }

    .project-image {
        width: 64px;
        height: 64px;
        border-radius: 12px;
        object-fit: contain;
        padding: 12px;
        background: rgba(52, 152, 219, 0.1);
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
        background: #3498db;
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

    @media (max-width: 768px) {
        .projectName {
            padding: 2rem 1rem;
        }
        
        h1 {
            font-size: 2rem;
        }
    }
</style>

<div class="projectName">
    <h1>Projects</h1>
    
    <div class="project-grid">
        <!-- GitHub Projects -->
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

        <!-- Azure Projects -->
        <!-- <div class="project-card"> -->
            <!-- <h3>Azure Projects</h3>
            <ul class="project-list">
                <li class="project-item">
                    <a href="https://dev.azure.com/stef663k/Svelte%20projects" class="project-link">
                        <img src={svelteImage} alt="Svelte" class="project-image" />
                        <div class="project-info">
                            <span>Svelte Projects</span>
                            <div class="project-description">Modern web applications using Svelte framework</div>
                        </div>
                    </a>
                </li>
                <li class="project-item">
                    <a href="https://dev.azure.com/stef663k/Zig%20projects" class="project-link">
                        <img src={zig} alt="Zig" class="project-image" />
                        <div class="project-info">
                            <span>Zig Projects</span>
                            <div class="project-description">System programming experiments with Zig</div>
                        </div>
                    </a>
                </li>
                <li class="project-item">
                    <a href="https://dev.azure.com/stef663k/FirstMauiApp" class="project-link">
                        <img src={maui} alt="MAUI" class="project-image" />
                        <div class="project-info">
                            <span>MAUI Portfolio</span>
                            <div class="project-description">Cross-platform portfolio application using .NET MAUI</div>
                        </div>
                    </a>
                </li>
            </ul>
        </div> -->
    </div>
</div>

