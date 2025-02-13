<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Quieres ser mi San Valentín?</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow: hidden;
            position: relative;
            transition: background-image 1s ease-in-out;
            background-size: cover;
            background-position: center;
            -webkit-backface-visibility: hidden;
        }
        h1 {
            font-size: 3em;
            font-family: 'Dancing Script', cursive;
            background: linear-gradient(45deg, #ff4e50, #fc913a);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.3);
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            font-size: 1.5em;
            padding: 12px 24px;
            margin: 10px;
            border: none;
            cursor: pointer;
            border-radius: 20px;
            transition: all 0.3s ease;
            font-weight: bold;
            box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
        }
        #yes {
            background-color: #ff4081;
            color: white;
        }
        #yes:hover {
            background-color: #e91e63;
            transform: scale(1.1);
        }
        #no {
            background-color: #ff5252;
            color: white;
            position: absolute;
        }
    </style>
</head>
<body>
    <h1>¿Quieres ser mi San Valentín?</h1>
    <div class="buttons">
        <button id="yes">Sí 💖</button>
        <button id="no">No 💔</button>
    </div>
    <audio id="background-music">
        <source src="https://docs.google.com/uc?export=download&id=1Xm2ylWdI-j2f2muqe7GJ9ZhtLksPtbBK" type="audio/mpeg">
        Tu navegador no soporta audio HTML5.
    </audio>
    <script>
        const images = [
            "https://i.imgur.com/1.jpg", "https://i.imgur.com/2.jpg",
            "https://i.imgur.com/3.jpg", "https://i.imgur.com/4.jpg",
            "https://i.imgur.com/5.jpg", "https://i.imgur.com/6.jpg",
            "https://i.imgur.com/7.jpg", "https://i.imgur.com/8.jpg",
            "https://i.imgur.com/9.jpg", "https://i.imgur.com/10.jpg",
            "https://i.imgur.com/11.jpg", "https://i.imgur.com/12.jpg",
            "https://i.imgur.com/13.jpg", "https://i.imgur.com/14.jpg",
            "https://i.imgur.com/15.jpg"
        ];
        
        let index = 0;
        function changeBackground() {
            document.body.style.backgroundImage = `url('${images[index]}')`;
            index = (index + 1) % images.length;
        }
        setInterval(changeBackground, 3000);
        
        const noButton = document.getElementById("no");
        
        noButton.addEventListener("mouseover", () => {
            const x = Math.random() * (window.innerWidth - noButton.clientWidth);
            const y = Math.random() * (window.innerHeight - noButton.clientHeight);
            noButton.style.left = `${x}px`;
            noButton.style.top = `${y}px`;
            noButton.style.transform = "translateZ(0)"; // Solución para Safari
        });
        
        document.body.addEventListener("click", () => {
            const bgMusic = document.getElementById("background-music");
            if (bgMusic.paused) {
                bgMusic.play().catch(error => console.log("Autoplay bloqueado en Safari"));
            }
        });
    </script>
</body>
</html>
