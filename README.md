# love-message
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Тайное послание</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #ffebcd;
            padding: 20px;
            overflow: hidden;
            position: relative;
        }
        #message {
            display: none;
            opacity: 0;
            transition: opacity 1.5s ease-in-out;
            margin-top: 20px;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        input, button {
            padding: 10px;
            margin-top: 10px;
            font-size: 16px;
        }
        img {
            width: 80%;
            max-width: 400px;
            border-radius: 10px;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <h2>Введите ваше ФИО:</h2>
    <input type="text" id="nameInput" placeholder="Фамилия Имя Отчество">
    <button onclick="checkName()">Проверить</button>

    <div id="message">
        <h2>Солнышко!</h2>
        <p>Ты — мое счастье, моя радость, моя нежность.</p>
        <p>Ты — мое вдохновение, мой свет в темноте, моя самая большая радость.</p>
        <p>Я люблю тебя всем сердцем и всегда буду рядом.</p>
        <h3>Ты — самое прекрасное, что есть в моей жизни ❤️</h3>

        <!-- Фото -->
        <img src="https://i.imgur.com/GWVed01.jpg" alt="Наше воспоминание">

        <!-- Таймер до 10 июля 2025 -->
        <p>До нашей годовщины осталось: <span id="countdown"></span></p>

        <!-- Кнопка "Ответить" -->
        <button onclick="sendMessage()">Ответить</button>
    </div>

    <script>
        function checkName() {
            var correctName = "Кожевникова Анна Владиславовна";
            var userInput = document.getElementById("nameInput").value.trim();

            if (userInput === correctName) {
                document.getElementById("message").style.display = "block";
                setTimeout(() => {
                    document.getElementById("message").style.opacity = "1";
                }, 100);
                countdown();
            } else {
                alert("Ошибка! Доступ запрещен.");
            }
        }

        function sendMessage() {
            let reply = prompt("Напиши что-нибудь в ответ 💌");
            if (reply) {
                alert("Спасибо за твой ответ! 💖");
            }
        }

        function countdown() {
            let eventDate = new Date("2025-07-10T00:00:00");
            let now = new Date();
            let diff = eventDate - now;

            let days = Math.floor(diff / (1000 * 60 * 60 * 24));
            document.getElementById("countdown").innerText = days + " дней";
        }
    </script>

</body>
</html>
