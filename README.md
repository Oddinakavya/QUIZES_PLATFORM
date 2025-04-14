# QUIZES_PLATFORM
TASK 5

COMPANY NAME: DYNAMITE WEBTECH

NAME: ODDINA KAVYA

INTERN ID: u75da

CODE :

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quiz Platform</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f0f0;
      padding: 20px;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
    }
    .question-form input,
    .question-form textarea {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .question-form button,
    .start-quiz-btn {
      padding: 10px 20px;
      margin: 10px 0;
      background-color: #007BFF;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .quiz {
      display: none;
    }
    .option {
      margin: 5px 0;
    }
    .feedback {
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Let's have some Brain Quizes</h2>
    <div class="question-form">
      <input type="text" id="question" placeholder="Enter your question....?">
      <input type="text" id="option1" placeholder="Option 1">
      <input type="text" id="option2" placeholder="Option 2">
      <input type="text" id="option3" placeholder="Option 3">
      <input type="text" id="option4" placeholder="Option 4">
      <input type="number" id="correctAnswer" placeholder="Correct option number (1-4)">
      <button onclick="addQuestion()">Add Question</button>
    </div>

    <button class="start-quiz-btn" onclick="startQuiz()">Let's Start Quiz</button>

    <div class="quiz" id="quiz"></div>
  </div>

  <script>
    let questions = [];
    let currentQuestionIndex = 0;

    function addQuestion() {
      const question = document.getElementById("question").value;
      const options = [
        document.getElementById("option1").value,
        document.getElementById("option2").value,
        document.getElementById("option3").value,
        document.getElementById("option4").value,
      ];
      const correct = parseInt(document.getElementById("correctAnswer").value) - 1;

      if (question && options.every(opt => opt) && correct >= 0 && correct < 4) {
        questions.push({ question, options, correct });
        alert("Question added!");
        document.querySelector('.question-form').reset();
      } else {
        alert("Please fill out all fields correctly.");
      }
    }

    function startQuiz() {
      if (questions.length === 0) {
        alert("Please add at least one question.");
        return;
      }
      document.querySelector('.question-form').style.display = 'none';
      document.querySelector('.start-quiz-btn').style.display = 'none';
      document.getElementById('quiz').style.display = 'block';
      showQuestion();
    }

    function showQuestion() {
      const quizContainer = document.getElementById('quiz');
      const q = questions[currentQuestionIndex];
      quizContainer.innerHTML = `
        <h3>${q.question}</h3>
        ${q.options.map((opt, i) => `
          <div class="option">
            <input type="radio" name="option" id="opt${i}" value="${i}">
            <label for="opt${i}">${opt}</label>
          </div>
        `).join('')}
        <button onclick="checkAnswer()">Submit Answer</button>
        <div class="feedback" id="feedback"></div>
      `;
    }

    function checkAnswer() {
      const selected = document.querySelector('input[name="option"]:checked');
      const feedback = document.getElementById("feedback");
      if (!selected) {
        feedback.textContent = "Please select an answer.";
        feedback.style.color = "red";
        return;
      }
      const answer = parseInt(selected.value);
      const correct = questions[currentQuestionIndex].correct;

      if (answer === correct) {
        feedback.textContent = "Correct!";
        feedback.style.color = "green";
      } else {
        feedback.textContent = `Wrong! Correct answer is: ${questions[currentQuestionIndex].options[correct]}`;
        feedback.style.color = "red";
      }

      setTimeout(() => {
        currentQuestionIndex++;
        if (currentQuestionIndex < questions.length) {
          showQuestion();
        } else {
          document.getElementById('quiz').innerHTML = `<h3>Quiz Completed!<br/>Let's Take some Break</h3>`;
        }
      }, 2000);
    }
  </script>
</body>
</html>


OUTPUT FOR TASK 5: QUIZES_PLATFORM
![Image](https://github.com/user-attachments/assets/b3375f0b-4fb4-442d-a325-c3cc70227fd5)

