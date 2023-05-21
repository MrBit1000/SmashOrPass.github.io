<!DOCTYPE html>
<html>
<head>
    <title>Smash or Pass Game</title>
    <style>
        body {
            text-align: center;
            font-family: 'Arial', sans-serif;
        }

        h1 {
            font-size: 36px;
            color: #ffffff;
            padding: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }

        img {
            max-width: 300px;
            margin-bottom: 20px;
        }

        .button-container {
            margin-top: 20px;
        }

        .button {
            padding: 15px 30px;
            font-size: 24px;
            margin: 0 10px;
            border-radius: 20px;
            color: #fff;
            border: none;
            cursor: pointer;
            outline: none;
            text-transform: uppercase;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }

        .smash-button {
            background-color: #4caf50;
        }

        .pass-button {
            background-color: #ff5252;
        }

        #result {
            display: none;
            margin-top: 30px;
        }

        img {
            width: 300px;
            height: 300px;
            object-fit: cover;
            margin-bottom: 20px;
            box-shadow: 0 0 10px 5px rgba(0, 0, 0, 0.2);
        }

        #score {
            font-size: 24px;
        }

        /* Animated background color */
        @keyframes bgAnimation {
            0% { background-color: #55a9f9; }
            50% { background-color: #448ef5; }
            100% { background-color: #55a9f9; }
        }

        body {
            animation: bgAnimation 4s infinite;
        }

        /* Falling emojis */
        @keyframes fall {
            0% {
                transform: translateY(-100vh);
                left: 0;
                opacity: 0;
            }
            100% {
                transform: translateY(100vh);
                left: calc(100vw * var(--x));
                opacity: 1;
            }
        }

        .falling-emojis {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            pointer-events: none;
            z-index: 9999;
        }

        .falling-emojis span {
            position: absolute;
            font-size: 24px;
            color: pink;
            animation: fall 5s linear infinite;
            transform: translateX(-50%);
        }
    </style>
</head>
<body>
    <h1>Smash or Pass Game</h1>
    <div id="game-container">
        <img id="celebrity-image" src="" alt="Celebrity Image">
        <div>
            <button id="smash-button" class="button smash-button" onclick="playGame('smash')">Smash</button>
            <button id="pass-button" class="button pass-button" onclick="playGame('pass')">Pass</button>
        </div>
    </div>
    <div id="result">
        <h2>Game Over!</h2>
        <p id="score"></p>
        <p id="comment"></p>
    </div>
    <div class="falling-emojis">
        <span style="--x: 0.1">💕</span>
        <span style="--x: 0.3">💕</span>
        <span style="--x: 0.5">💕</span>
        <span style="--x: 0.7">💕</span>
        <span style="--x: 0.9">💕</span>
    </div>

    <script>
        // Array of celebrity images
        var celebrities = [
            "images/alanna masterson.jpeg",
            "images/Kimmi.jpeg",
            "images/amber heard.jpeg",
            "images/kloe kardasion.jpeg",
            "images/lady gaga.jpeg",
            "images/jennifer lawrence.jpeg",
            "images/zendaya.jpeg",
            "images/taylor swift.jpeg",
            "images/selena gomez.jpeg",
            "images/sarah wayne callies.jpeg",
            "images/jennifer aniston.jpeg",
            "images/hailey bieber.jpeg",
            "images/emily kinney.jpeg",
            "images/emma watson.jpeg",
            "images/anne hathaway.jpeg",
            "images/danai gurira.jpeg",
            "images/jenna ortega.png",
            "images/ariana grande.jpeg",
            // Add more celebrity objects with image and name
        ];

        var score = 0;
        var currentIndex = 0;

        function playGame(action) {
            if (action === "smash") {
                score++;
            }
            currentIndex++;
            if (currentIndex < celebrities.length) {
                showNextCelebrity();
            } else {
                showResult();
            }
        }

        function showNextCelebrity() {
            var celebrityImage = document.getElementById("celebrity-image");
            celebrityImage.src = celebrities[currentIndex];
        }

        function showResult() {
            var gameContainer = document.getElementById("game-container");
            var resultContainer = document.getElementById("result");
            var scoreElement = document.getElementById("score");
            var commentElement = document.getElementById("comment");

            gameContainer.style.display = "none";
            resultContainer.style.display = "block";
            scoreElement.textContent = "Your score: " + score;

            if (score === celebrities.length) {
                commentElement.textContent = "Perfect score! You're a real chad!";
            } else if (score > celebrities.length / 2) {
                commentElement.textContent = "Man you pullin' hard. phew lucky it's not me.";
            } else if (score > 0) {
                commentElement.textContent = "Eh probably average. You deserve what you got.";
            } else {
                commentElement.textContent = "Man get some better taste!";
            }
        }

        showNextCelebrity();
    </script>
</body>
</html>
