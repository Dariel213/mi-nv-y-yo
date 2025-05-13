# mi-nv-y-yo
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Juego para Mi Amor</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #ffe6f0;
      color: #333;
      text-align: center;
      padding: 20px;
    }
    .question {
      margin: 20px 0;
    }
    .result {
      margin-top: 20px;
      font-weight: bold;
      color: green;
    }
    button {
      padding: 10px 20px;
      margin: 10px;
      cursor: pointer;
      background-color: #ff99cc;
      border: none;
      border-radius: 5px;
    }
  </style>
</head>
<body>

  <h1>💖 ¿Cuánto me conoces, mi amor? 💖</h1>

  <div class="question" id="questionContainer"></div>
  <div class="result" id="result"></div>

  <script>
    const questions = [
      {
        question: "¿Cuál es mi comida favorita?",
        options: ["Pizza", "Sushi", "Arepas", "Tacos"],
        answer: "Sushi"
      },
      {
        question: "¿Qué día empezamos a hablar por primera vez?",
        options: ["10 de enero", "14 de febrero", "25 de marzo", "31 de diciembre"],
        answer: "25 de marzo"
      },
      {
        question: "¿Qué me hace más feliz?",
        options: ["Dormir", "Programar", "Estar contigo", "Ver películas"],
        answer: "Estar contigo"
      }
    ];

    let currentQuestion = 0;
    let score = 0;

    function showQuestion() {
      const container = document.getElementById('questionContainer');
      container.innerHTML = '';
      if (currentQuestion < questions.length) {
        const q = questions[currentQuestion];
        const qElem = document.createElement('div');
        qElem.innerHTML = `<h3>${q.question}</h3>`;
        q.options.forEach(option => {
          const btn = document.createElement('button');
          btn.innerText = option;
          btn.onclick = () => checkAnswer(option);
          qElem.appendChild(btn);
        });
        container.appendChild(qElem);
      } else {
        document.getElementById('result').innerText = `¡Terminaste! Tu puntuación: ${score}/${questions.length} 💕`;
        if (score === questions.length) {
          const msg = document.createElement('div');
          msg.innerHTML = `<p>¡Lo sabías todo! 🥰 Eres la persona más especial para mí. Te amo mucho ❤️</p>`;
          document.body.appendChild(msg);
        }
      }
    }

    function checkAnswer(selected) {
      if (selected === questions[currentQuestion].answer) {
        score++;
      }
      currentQuestion++;
      showQuestion();
    }

    showQuestion();
  </script>

</body>
</html>
