Quiz App

Welcome to the Quiz App! This application allows users to participate in quizzes of three categories (Music, Modern Art, Coding) and test their knowledge on these topics.

This README file provides essential information about the app, including its features, setup instructions, and usage guidelines.



Features
1.	This app allows the users to choose from three pre-defined quizzes on different topics.
2.	Quiz consists of ten questions with multiple choices, from which the users can select one correct option.
3.	The app tracks the score of the correct answer, which is displayed at the end of the quiz.



Importing Data
The data for the questions and the answers have been imported from JS file,  



Landing Page

The landing page consists of the heading (quiz pop) and three buttons. User can select among the three topics using the topics.

<body>
    <!-- Start Page -->
    <div class="start">
        <h2>Welcome to the Quiz </h2>
        <a href="./quizStart.html">
            <div class="buttons">
                <Button id="start-btn">Start</Button>
            </div>
         </a>
    </div>
</body>







Game Page
1.	The game page consists of ten questions, where the the user can select only one option.
2.	User can go to next question using next button and to the previous question using the previous button.
3.	User can end the the quiz by clicking on the submit button at the end of the quiz.
4.	Users can see their scores at the end of the quiz(when they click on submit button).



<div id="quiz-container" class="quiz-container">
      <h2 id="category-title" class="category-title"></h2>
      <p id="question-text" class="question-text"></p>
      <div id="options-container" class="options-container">
      </div>
      <div class="navigation-buttons">
        <button id="prev-button">Previous</button>
        <button id="next-button">Next</button>
        <button id="submit-button" class="submit-button">Submit</button>
      </div>


Variables and DOM Elements

The code consists several variables and constants to store information about current question and the number of questions. The following DOM elements are also accessed and stored in constants:
 questionELement, optionsElemet, selectedOption,

Event listeners are used for button actions namely previousButton, nextButton, submitButton.

Starting the quiz and load topic
// Function to load the topic selection
    function loadTopicSelection() {
      const musicButton = document.getElementById("musicButton");
      const artButton = document.getElementById("artButton");
      const codingButton = document.getElementById("codingButton");

      musicButton.addEventListener("click", function() {
        localStorage.setItem("quizTopic", "Music");
        startQuiz();
      });

      artButton.addEventListener("click", function() {
        localStorage.setItem("quizTopic", "Modern-Art");
        startQuiz();
      });

      codingButton.addEventListener("click", function() {
        localStorage.setItem("quizTopic", "Coding");
        startQuiz();
      });
    }
// Load the topic selection
    loadTopicSelection();


Function loadToppicSelection is used to start the game, where the user lands on the page with categories to select from, which is handled by loadTopicSelection function. The event listener functions will take to the selected category page.


Start Game

    // Function to start the quiz
    function startQuiz() {
      currentQuestion = 0;
      score = 0;
      loadQuestion();
    }
Function startQuiz is used to start quiz.

 

Loading questions

function loadQuestion() {
      const questionElement = document.getElementById("question");
      const optionsElement = document.getElementById("options");
      const question = data[localStorage.getItem("quizTopic")][currentQuestion].question;
      const options = data[localStorage.getItem("quizTopic")][currentQuestion].options;

      questionElement.innerHTML = question;
      optionsElement.innerHTML = "";

      for (let i = 0; i < options.length; i++) {
        const option = document.createElement("button");
        option.innerHTML = options[i];
        option.addEventListener("click", function() {
          selectOption(this);
        });
        optionsElement.appendChild(option);
      }
    }

The questions are displayed to the user using function loadQuestion, 



Selecting Options

function selectOption(option) {
      const options = document.getElementById("options").getElementsByTagName("button");

      for (let i = 0; i < options.length; i++) {
        options[i].classList.remove("selected");
      }

      option.classList.add("selected");
    }
 

The function selectOption is used to record the option selected by the user.



Next question
// Function to load the next question
function loadNextQuestion() {
      const optionsElement = document.getElementById("options");
      const selectedOption = optionsElement.getElementsByClassName("selected")[0];
      const answer = data[localStorage.getItem("quizTopic")][currentQuestion].answer;

The function loadNextQuestion  is used to load the next question when clicked on the next button by the user.



Storage of Score
localStorage.setItem("quizScore", score);
      } else {
        loadQuestion();
      }
All the scores that are recorded  are stored in the localStorage  in the QuizScore.










