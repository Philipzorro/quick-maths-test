<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quick Maths Test</title>
    <style>
        body { font-family: sans-serif; text-align: center; background: #fafafa; padding: 20px; }
        .card { background: white; padding: 30px; border-radius: 15px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); display: inline-block; min-width: 300px; }
        #question { font-size: 2.5rem; margin: 20px 0; color: #5b2e91; } /* Pi Purple */
        input { font-size: 1.5rem; width: 80px; text-align: center; padding: 5px; border: 2px solid #ccc; border-radius: 5px; }
        #timer { font-weight: bold; color: red; font-size: 1.2rem; }
        #score { color: #555; margin-bottom: 10px; }
    </style>
</head>
<body>

    <div class="card">
        <div id="score">Score: 0</div>
        <div id="timer">Time: 10s</div>
        <div id="question">1 + 3 = ?</div>
        <input type="number" id="answer" autofocus placeholder="?">
    </div>

    <script>
        let score = 0;
        let timeLeft = 10;
        let correctAnswer;

        const questionEl = document.getElementById('question');
        const answerInput = document.getElementById('answer');
        const scoreEl = document.getElementById('score');
        const timerEl = document.getElementById('timer');

        function generateQuestion() {
            let num1 = Math.floor(Math.random() * 10) + 1;
            let num2 = Math.floor(Math.random() * 10) + 1;
            correctAnswer = num1 + num2;
            questionEl.innerText = `${num1} + ${num2} = ?`;
            answerInput.value = '';
        }

        answerInput.addEventListener('input', () => {
            if (parseInt(answerInput.value) === correctAnswer) {
                score++;
                scoreEl.innerText = `Score: ${score}`;
                timeLeft = 10; // Reset timer on correct answer
                generateQuestion();
            }
        });

        setInterval(() => {
            if (timeLeft > 0) {
                timeLeft--;
                timerEl.innerText = `Time: ${timeLeft}s`;
            } else {
                alert("Game Over! Final Score: " + score);
                score = 0;
                timeLeft = 10;
                generateQuestion();
            }
        }, 1000);

        generateQuestion();
    </script>
</body>
</html>
