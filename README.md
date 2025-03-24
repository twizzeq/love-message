# love-message
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Мета-тег для мобильных устройств -->
    <title>Тайное послание</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f7c8d6; /* Нежно-розовый фон */
            padding: 20px;
            overflow-y: scroll; /* Добавляем прокрутку */
            position: relative;
            min-height: 100vh;
        }
        #message {
            display: none;
            opacity: 1;
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
            border-radius: 5px;
            border: 1px solid #ccc;
            transition: background-color 0.3s;
        }
        input:focus, button:focus {
            outline: none;
            border-color: #ff69b4;
        }
        button {
            background-color: #ff69b4;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #ff1493;
        }
        img {
            width: 80%;
            max-width: 400px;
            border-radius: 10px;
            margin-top: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* Полароидный стиль */
        }

        /* Стиль для полароидного фото */
        .polaroid {
            display: inline-block;
            padding: 10px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            transform: rotate(-5deg);
        }

        /* Стиль для жирного текста до годовщины */
        .bold {
            font-weight: bold;
        }

        /* Стиль для области для ответа */
        #responseSection {
            display: none;
            margin-top: 20px;
            text-align: center;
        }
        #responseMessage {
            width: 80%;
            max-width: 400px;
            margin-top: 10px;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 16px;
            resize: none;
        }
    </style>
</head>
<body>

    <h2>Введите ваше ФИО:</h2>
    <input type="text" id="nameInput" placeholder="Введите ваше ФИО" oninput="validateName()">
    <button id="openMessageButton" onclick="checkName()" disabled>Открыть послание</button>

    <div id="message">
        <h2>Мое солнышко!</h2>
        <p>Ты — моё счастье, моя радость, моя нежность. С каждым днём я всё больше осознаю, как невероятно повезло мне найти тебя.</p>
        <p>Я люблю тебя всем сердцем и всегда буду рядом. В твоих глазах я вижу целый мир, полный света и гармонии. Ты для меня — самое ценное, что есть в этой жизни, и я готов делать всё, чтобы ты была счастлива.</p>
        <p>Ты — моя опора, моя вдохновительница, моя любовь. Без тебя мир был бы не таким ярким. Ты — моя любовь и моя судьба. С каждым днём я всё больше убеждаюсь, что встретил тебя не случайно. Ты — мой идеал, моя поддержка и моё счастье. Ты — самое прекрасное, что есть в моей жизни ❤️.</p>
        <h3>Я люблю тебя, и ничего в этом мире не может изменить мои чувства. Ты — единственная, моя дорогая. ❤️</h3>

        <!-- Заменяем видео на фото -->
        <div class="polaroid">
            <img src="https://imgur.com/ROc6Nqt.jpg" alt="Наше воспоминание">
        </div>

        <p>До нашей годовщины осталось: <span id="countdown" class="bold"></span></p>
        
        <!-- Форма для ответа -->
        <div id="responseSection">
            <h3>Ваш ответ:</h3>
            <textarea id="responseMessage" placeholder="Введите ваш ответ..." rows="4"></textarea>
            <br>
            <button onclick="sendResponse()">Отправить ответ</button>
            <p id="responseText"></p>
        </div>
    </div>

    <script>
        function validateName() {
            // Проверка, чтобы было введено полное ФИО
            const nameInput = document.getElementById('nameInput').value;
            const button = document.querySelector("#openMessageButton");
            // Регулярное выражение для проверки строго "Кожевникова Анна Владиславовна"
            const regex = /^Кожевникова\s+[А-ЯЁ][а-яё]*\s+[А-ЯЁ][а-яё]*$/;
            if (regex.test(nameInput)) {
                button.disabled = false;  // Включить кнопку, если введено полное ФИО
            } else {
                button.disabled = true;   // Выключить кнопку, если введено неправильное ФИО
            }
        }

        function checkName() {
            // Показ открытки, если введено полное ФИО
            const nameInput = document.getElementById('nameInput').value;
            if (nameInput.trim() !== '') {
                document.getElementById('message').style.display = 'block';  // Показываем сообщение
                startCountdown();
                document.getElementById('responseSection').style.display = 'block';  // Показываем форму для ответа
            } else {
                alert('Пожалуйста, введите ваше полное ФИО!');
            }
        }

        function startCountdown() {
            // Дата годовщины
            var anniversaryDate = new Date("2025-05-21T00:00:00").getTime();

            var countdown = setInterval(function() {
                var now = new Date().getTime();
                var timeLeft = anniversaryDate - now;

                var days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
                var hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                var minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                var seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

                document.getElementById("countdown").innerHTML = days + "дн " + hours + "ч " + minutes + "м " + seconds + "с ";

                if (timeLeft < 0) {
                    clearInterval(countdown);
                    document.getElementById("countdown").innerHTML = "Годовщина наступила!";
                }
            }, 1000);
        }

        function sendResponse() {
            const responseMessage = document.getElementById('responseMessage').value;
            const responseText = document.getElementById('responseText');
            if (responseMessage.trim() !== '') {
                responseText.innerHTML = `<strong>Ваш ответ:</strong><p>${responseMessage}</p>`;
                document.getElementById('responseMessage').value = '';  // Очищаем поле ввода
            } else {
                alert("Пожалуйста, введите ваше сообщение!");
            }
        }
    </script>

</body>
</html>
