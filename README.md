<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine? ❤️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;700&display=swap');

        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            text-align: center;
            background-color: #ffebf0;
            color: #d63384;
            overflow: hidden;
        }

        .section {
            position: absolute;
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            transition: opacity 1s ease-in-out;
        }

        .hearts, .confetti-container {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
        }

        .heart, .confetti {
            position: absolute;
            color: red;
            font-size: 50px;
            animation: floatUp 3s linear infinite;
        }

        .confetti {
            background-color: #ff477e;
            width: 10px;
            height: 10px;
            border-radius: 50%;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) rotate(0); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        .text {
            font-size: 2.5rem;
            opacity: 0;
            font-family: 'Pacifico', cursive;
            position: absolute;
            animation: fadeInOut 2s linear forwards;
        }

        @keyframes fadeInOut {
            0% { opacity: 0; transform: scale(0.8); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; }
        }

        #text1 { animation-delay: 1s; }
        #text2 { animation-delay: 4s; }

        .next-btn {
            background-color: #d63384;
            color: white;
            padding: 15px 30px;
            border: none;
            font-size: 18px;
            border-radius: 5px;
            cursor: pointer;
            position: absolute;
            bottom: 100px;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }

        .next-btn.show {
            opacity: 1;
        }

        #secondSection {
            opacity: 0;
            pointer-events: none;
        }

        .container {
            max-width: 600px;
            padding: 20px;
            background: white;
            border-radius: 15px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        .valentine-btn {
            background-color: #ff477e;
            color: white;
            padding: 15px 20px;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            margin: 10px;
            transition: 0.3s;
        }

        .valentine-btn:hover {
            background-color: #e6396d;
        }
    </style>
</head>
<body>

    <div id="firstSection" class="section">
        <div class="hearts"></div>
        <div class="text" id="text1">Hey bestie ❤️</div>
        <div class="text" id="text2">I have something to ask you... 💕</div>
        <button id="nextButton" class="next-btn" onclick="showSecondPage()">Next →</button>
    </div>

    <div id="secondSection" class="section">
        <div class="confetti-container"></div>
        <div class="container">
            <h1>Will you be my Valentine? ❤️</h1>
            
            <!-- Google Drive Video Embed -->
            <iframe id="valentineVideo" width="400" height="300" src="https://drive.google.com/file/d/1VJ60zst2qzavTZcNEqQK5FqSOWMG-NKF/preview" allow="autoplay" frameborder="0" allowfullscreen></iframe>

            <div>
                <button class="valentine-btn" onclick="celebrate()">Hell Yeah! 🎉</button>
                <button class="valentine-btn" onclick="celebrate()">I would love to! ❤️</button>
            </div>
        </div>

        <audio id="bgMusic" loop>
            <source src="path-to-your-music.mp3" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            document.querySelector('.hearts').appendChild(heart);

            let size = Math.random() * 50 + 20;
            heart.style.fontSize = `${size}px`;
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.animationDuration = Math.random() * 2 + 3 + "s";

            setTimeout(() => { heart.remove(); }, 4000);
        }
        setInterval(createHeart, 200);

        function createConfetti() {
            const confetti = document.createElement('div');
            confetti.classList.add('confetti');
            document.querySelector('.confetti-container').appendChild(confetti);

            let size = Math.random() * 10 + 5;
            confetti.style.width = `${size}px`;
            confetti.style.height = `${size}px`;
            confetti.style.left = Math.random() * 100 + "vw";
            confetti.style.animationDuration = Math.random() * 2 + 3 + "s";

            setTimeout(() => { confetti.remove(); }, 4000);
        }

        function showSecondPage() {
            document.getElementById("firstSection").style.opacity = "0";
            setTimeout(() => {
                document.getElementById("firstSection").style.display = "none";
                document.getElementById("secondSection").style.opacity = "1";
                document.getElementById("secondSection").style.pointerEvents = "all";
                document.getElementById("bgMusic").play();
            }, 1000);
        }

        function celebrate() {
            // Start confetti animation
            setInterval(createConfetti, 100);

            // Close the website after 2 seconds
            setTimeout(() => {
                window.close();
            }, 2000);
        }

        // Close the site after the video ends
        document.getElementById("valentineVideo").onended = function() {
            document.querySelector(".valentine-btn").style.display = "block";
        };

        setTimeout(() => {
            document.getElementById("nextButton").classList.add("show");
        }, 5000);
    </script>

</body>
</html>
