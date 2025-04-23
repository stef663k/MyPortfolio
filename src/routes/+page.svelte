<script>
    
</script>

<head>
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
            .mainName h1{
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
    <title>Home</title>
</head>

<body>
    <div class="welcome-text">
        <div class="mainName">
             <h1>Welcome to Stefan's portfolio</h1>
        </div>
        <div class="aboutme">
            <p>
                I'm a 36 year old guy, who decided to switch day job out with the books during a pandemic. I started learning c# and,
                I got a couple of projects under the project tap, where you can see them on github. 
                There will come more projects on there as i make them. 
                I also started dabling in Zig and Unity. 
                This website was made with sveltekit.
            
            </p>
        </div>
    </div>
</body>

