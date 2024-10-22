<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Practica las Tablas de Multiplicar - Fútbol</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            background: url('https://image.shutterstock.com/image-photo/green-grass-soccer-field-background-260nw-1939575085.jpg') no-repeat center center fixed;
            background-size: cover;
        }
        .scoreboard {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
        }
        .ball-icon {
            width: 50px;
            height: 50px;
            background-image: url('https://upload.wikimedia.org/wikipedia/commons/d/d3/Soccerball.svg');
            background-size: contain;
            display: inline-block;
        }
    </style>
</head>
<body class="flex flex-col items-center justify-center h-screen text-center text-white">
    <div class="p-8 rounded-lg shadow-lg scoreboard">
        <h1 class="text-4xl font-bold mb-4">¡Practica las Tablas de Multiplicar!</h1>
        <div class="text-2xl font-semibold mb-2">
            <span id="multiplicand"></span> x <span id="multiplier"></span>
        </div>
        <input type="number" id="userAnswer" class="p-2 text-center rounded" placeholder="Escribe tu respuesta">
        <button onclick="checkAnswer()" class="mt-4 p-2 bg-green-500 rounded text-white hover:bg-green-700 transition-all">Responder</button>
        <p id="message" class="mt-4 text-xl"></p>
        <div class="mt-6">
            <p><span class="ball-icon"></span> Aciertos: <span id="correctCount">0</span></p>
            <p><span class="ball-icon"></span> Fallos: <span id="incorrectCount">0</span></p>
        </div>
    </div>

    <script>
        let correctCount = 0;
        let incorrectCount = 0;
        let multiplicand, multiplier;

        function generateMultiplication() {
            multiplicand = Math.floor(Math.random() * 10) + 1;
            multiplier = Math.floor(Math.random() * 10) + 1;
            document.getElementById("multiplicand").innerText = multiplicand;
            document.getElementById("multiplier").innerText = multiplier;
            document.getElementById("userAnswer").value = '';
            document.getElementById("message").innerText = '';
        }

        function checkAnswer() {
            const userAnswer = parseInt(document.getElementById("userAnswer").value);
            const correctAnswer = multiplicand * multiplier;

            if (userAnswer === correctAnswer) {
                correctCount++;
                document.getElementById("message").innerText = "¡Correcto! ⚽️ ¡Bien hecho!";
                document.getElementById("message").classList.add("text-green-500");
                document.getElementById("message").classList.remove("text-red-500");
            } else {
                incorrectCount++;
                document.getElementById("message").innerText = "¡Incorrecto! ❌ Inténtalo de nuevo.";
                document.getElementById("message").classList.add("text-red-500");
                document.getElementById("message").classList.remove("text-green-500");
            }

            document.getElementById("correctCount").innerText = correctCount;
            document.getElementById("incorrectCount").innerText = incorrectCount;
            generateMultiplication();
        }

        // Inicializamos la primera multiplicación
        generateMultiplication();
    </script>
</body>
</html>
