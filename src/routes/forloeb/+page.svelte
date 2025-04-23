<script>
    import { text } from "@sveltejs/kit";
    import { onMount } from "svelte";

     
    const currentDate = new Date();

       /**
     * @type {{ [key: string]: { date: Date, name: string } }}
     */
    const dates = {
        G2: { date: new Date('2021-01-18'), name: "Grundforløb 2" },
        P1: { date: new Date('2021-09-15'), name: "Praktikforløb 1" },
        H1: { date: new Date('2022-02-28'), name: "Hovedforløb 1" },
        P2: {date: new Date('2022-05-12'), name: "Praktikforløb 2"},
        H2: {date: new Date('2022-08-01'), name: "Hovedforløb 2"},
        P3: {date: new Date('2022-10-08'), name: "Praktikforløb 3"},
        H3: {date: new Date('2023-10-09'), name: "Hovedforløb 3"},
        P4: {date: new Date('2023-12-16'), name: "Praktikforløb 4"},
        H4: {date: new Date('2024-10-07'), name: "Hovedforløb 4"},
        P5: {date: new Date('2024-10-16'), name: "Praktikforløb 5"},
        H5: {date: new Date('2025-01-29'), name: "Hovedforløb 5"},
        P6: {date: new Date('2025-03-24'), name: "Praktikforløb 6"},
        H6: {date: new Date('2025-10-20'), name: "Hovedforløb 6"},
        p7: {date: new Date('2025-11-22'), name: "Praktikforløb 7"},
        Slut: {date: new Date('2026-03-05'), name: "Færdiguddannet"}
    };

    /**
     * @param {Date} date 
     * @returns {string} 
     */
    function formatDate(date) {
        const year = date.getFullYear();
        const month = String(date.getMonth() + 1).padStart(2, '0');
        const day = String(date.getDate()).padStart(2, '0');
        return `${year}-${month}-${day}`;
    }

    onMount(() => {
        for (const key in dates) {
            if (dates.hasOwnProperty(key)) {
                const course = dates[key];
                const element = document.getElementById(`date${key}`);
                if (element) {
                    if (key === 'P6') {
                        element.classList.add("current");
                    } else if (currentDate >= course.date || 
                             ['G2', 'P1', 'H1', 'P2', 'H2', 'P3', 'H3', 'P4', 'H4', 'P5', 'H5'].includes(key)) {
                        element.classList.add("completed");
                    } else {
                        element.classList.add("upcoming");
                    }
                }
            }
        }
    });

</script>
<title>Forløb</title>
<header>
    <style>
        :global(body) {
            background-color: #f8f9fa;
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
            margin: 0;
            padding: 0;
            color: #2d3436;
        }

        .forloeb {
            display: flex;
            justify-content: center;
            padding: 4rem 0 3rem;
            background: linear-gradient(135deg, #4d0b8a 0%, #8a2be2 50%, #60219a 100%);
            color: white;
            margin: 0;
            position: relative;
            overflow: hidden;
        }

        .forloeb::before {
            content: '';
            position: absolute;
            width: 150%;
            height: 150%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, rgba(0,0,0,0.1) 100%);
            pointer-events: none;
        }

        .forloeb h1 {
            font-size: 2.75rem;
            margin: 0;
            font-weight: 700;
            letter-spacing: -0.5px;
            position: relative;
            z-index: 1;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }

        .timeline-container {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 2.5rem;
            margin: -2.5rem auto 3rem;
            max-width: 1000px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            position: relative;
        }

        .dates {
            display: flex;
            flex-direction: column;
            gap: 1.25rem;
            position: relative;
        }

        .timeline-item {
            padding: 1.5rem 2rem;
            margin: 0.5rem 0;
            border-radius: 16px;
            color: white;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            gap: 1.5rem;
            background: #ffffff;
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 4px;
            background: rgba(138, 43, 226, 0.6);
            transition: width 0.3s ease;
        }

        .timeline-item:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 16px rgba(0,0,0,0.12);
            background: rgba(138, 43, 226, 0.1);
        }

        .timeline-item:hover::before {
            width: 6px;
        }

        .status-indicator {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            flex-shrink: 0;
        }

        .item-content {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            gap: 0.25rem;
        }

        .date {
            font-size: 0.9rem;
            color: #636e72;
            font-weight: 500;
        }

        .name {
            font-size: 1.1rem;
            font-weight: 600;
            color: #2d3436;
        }
/* 
        .completed {
            background: #ffffff;
        } */

        .completed .status-indicator {
            background: #9eacad;
        }

        .completed::after {
            content: 'Afsluttet';
            font-style: italic;
            color: #95a5a6;
            position: absolute;
            right: 2rem;
            top: 50%;
            transform: translateY(-50%);
        }

        .current {
            background: rgba(138, 43, 226, 0.6);
            border-color: blueviolet;
        }
        .current:hover{
            background: rgba(138, 43, 226, 0.5);
        }

        .current .date {
            color: rgba(255,255,255,0.9);
        }

        .current .name {
            color: white;
        }

        .current .status-indicator {
            background: #ffffff;
            box-shadow: 0 0 0 3px rgba(255,255,255,0.2);
        }

        .upcoming {
            background: #ffffff;
        }

        .upcoming .status-indicator {
            background: #dcdde1;
        }

        @keyframes itemEntrance {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
        }

        .timeline-item {
            animation: itemEntrance 0.6s ease-out forwards;
            animation-delay: calc(var(--index) * 0.1s);
            opacity: 0;
        }

        @media (max-width: 480px){
            .forloeb h1 {
                font-size: 1.5rem;
                padding: 0.1rem;
                text-align: center;
            }

            .timeline-container {
                margin: -2rem auto 2rem;
                padding: 1rem;
                text-align: left;
            }

            .timeline-item {
                padding: 1rem;
                flex-direction: row;
                align-items: center;
                gap: 0.75rem;
            }

            .completed::after {
                font-size: 0.8rem;
                right: 0.75rem;
                opacity: 0.8;
            }

            .item-content {
                padding-right: 4rem;
            }
        }

        @media (max-width: 768px) {
            .forloeb h1 {
                font-size: 2rem;
                padding: 0 1rem;
                text-align: center;
            }

            .timeline-container {
                margin: -2rem auto 2rem;
                padding: 1.5rem;
                border-radius: 16px;
            }

            .timeline-item {
                padding: 1.25rem;
                flex-direction: row;
                align-items: center;
                gap: 1rem;
            }

            .completed::after {
                right: 1rem;
                font-size: 0.9rem;
            }
        }

        @media (min-width: 769px) {
            :global(::-webkit-scrollbar) {
                width: 8px;
            }

            :global(::-webkit-scrollbar-track) {
                background: rgba(0,0,0,0.05);
            }

            :global(::-webkit-scrollbar-thumb) {
                background: #3498db;
                border-radius: 4px;
            }
        }
    </style>
</header>

<div class="forloeb">
    <h1>Uddannelsesforløb</h1>
</div>

<div class="timeline-container">
    <div class="dates">
        {#each Object.keys(dates) as key, index}
            <div 
                id="date{key}" 
                class="timeline-item {key}"
                style="--index: {index}"
            >
                <div class="status-indicator"></div>
                <div class="item-content">
                    <div class="date">{formatDate(dates[key].date)}</div>
                    <div class="name">{dates[key].name}</div>
                </div>
            </div>
        {/each}
    </div>
</div>