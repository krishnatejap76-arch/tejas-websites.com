<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Kutti ❤️</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: #fff0f3; /* Soft pinkish white */
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Continuous Floating Background */
        .bg-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .float-icon {
            position: absolute;
            bottom: -50px;
            opacity: 0.6;
            animation: moveUp 5s linear infinite;
        }

        @keyframes moveUp {
            to {
                transform: translateY(-110vh) rotate(360deg);
            }
        }

        /* Main Card */
        .card {
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 20px 50px rgba(255, 77, 109, 0.3);
            text-align: center;
            border: 5px solid #ff4d6d;
            z-index: 10;
            width: 320px;
            position: relative;
        }

        h1 {
            color: #ff4d6d;
            font-size: 1.8rem;
            margin-bottom: 40px;
            line-height: 1.4;
        }

        .buttons {
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 100px;
        }

        button {
            padding: 15px 30px;
            font-size: 1.1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        #yesBtn {
            background: #ff4d6d;
            color: white;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
        }

        /* The No Button - Absolute so it can fly anywhere */
        #noBtn {
            background: #adb5bd;
            color: white;
            position: fixed; /* Important for escaping */
            z-index: 999;
        }

        #success {
            display: none;
        }

        .love-text {
            color: #d63384;
            font-size: 1.5rem;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="bg-container" id="bg"></div>

    <div class="card" id="mainCard">
        <div id="ask">
            <h1>ramya will you be my valentine? 💕</h1>
            <div class="buttons">
                <button id="yesBtn">Yes! ❤️</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div id="success">
            <p class="love-text">best decision ever 🙌<br><br> I LOVE YOU 🥰😘</p>
            <div style="font-size: 3rem; margin-top: 20px;">🧸🎈💖✨</div>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const askDiv = document.getElementById('ask');
        const successDiv = document.getElementById('success');
        const bg = document.getElementById('bg');

        // --- 1. THE ESCAPING LOGIC ---
        // Every time she hovers or touches, it jumps instantly
        const escape = () => {
            const padding = 50;
            const maxX = window.innerWidth - noBtn.offsetWidth - padding;
            const maxY = window.innerHeight - noBtn.offsetHeight - padding;
            
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);
            
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        };

        noBtn.addEventListener('mouseover', escape);
        noBtn.addEventListener('click', escape); // In case she is very fast
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            escape();
        });

        // --- 2. THE BACKGROUND DECORATION ---
        const icons = ['❤️', '🧸', '🎈', '💖', '🧸', '✨', '🎈'];
        function addIcon() {
            const icon = document.createElement('div');
            icon.className = 'float-icon';
            icon.innerText = icons[Math.floor(Math.random() * icons.length)];
            icon.style.left = Math.random() * 100 + 'vw';
            icon.style.fontSize = (Math.random() * 20 + 20) + 'px';
            icon.style.animationDuration = (Math.random() * 3 + 3) + 's';
            bg.appendChild(icon);
            
            // Remove after animation to save memory
            setTimeout(() => icon.remove(), 5000);
        }
        setInterval(addIcon, 300); // Creates an icon every 300ms

        // --- 3. THE YES CLICK ---
        yesBtn.addEventListener('click', () => {
            askDiv.style.display = 'none';
            noBtn.style.display = 'none';
            successDiv.style.display = 'block';
            
            // Celebration effect
            setInterval(addIcon, 50); 
            document.body.style.background = "#ffc1cf";
        });
    </script>
</body>
</html>
