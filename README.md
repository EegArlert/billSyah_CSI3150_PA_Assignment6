# billSyah_CSI3150_PA_Assignment6

# Demo Quiz App

## Lesson Outcomes

After implementing this project, you will have an understanding of: 

- Createn a fully functioning app by using Vanilla JS
- Linking multiple JS file into main HTML file
- Styling using CSS for responsive design
- DOM manipulation
- JS Concepts:
    - Event listeners
    - Timers (setInterval and clearInterval)
    - Array manipulation
    - Functions and closures
- Integrating Font Awesome into the project
- Patience

## Revision Topics

- Linking JS and HTML file using script tag
- Linking CSS and HTML file using link tag

### Pre-requisites

- This project will require VSCode to be installed on your computer

### App Functionality 

- Interactive Quiz Interface:
    - The app shows multiple-choice questions as you go through the quiz.
    - It marks your selected answers as correct or incorrect with easy-to-see feedback.

- Real-Time Timer:
    - Each question has a 15-second countdown to keep things moving.
    - If you don't answer in time, it picks the correct answer for you automatically.
    
- Scoring and Progress Tracking:
    - Keeps track of how many answers you get right and your progress through the quiz.
    - Shows a final score with fun, custom messages based on how well you did.

- Responsive Design:
    - Looks great no matter what screen size you're on, thanks to CSS.

- Dynamic Content:
    - All the questions and answers are pulled from a JavaScript file and pop up on the screen dynamically as you play.


### Directory Structure

 - The application is organize into the following directory structure:

    ```
    demo-quizz-app/
    |--- index.html
    |--- css/
        |--- styles.css
    |--- js/
        |--- questions.js
        |--- quizApp.js
    |--- .gitignore
    |--- README.md

    ```
        

### File Linkage and Overview

- index.html:
    - This is the main file where the link between html, css, and js are being instantiated
    - Font Awesome is also being linked here
    - There are placeholders in this file for things like the questions, timer, and results, which get filled in dynamically when you use the app

- style.css:
    - This is where the styling of the app being specified

- question.js:
    - This file act as a storage of all the questions objects. The question objects attributes are:
       - The question itself
       - Multiple-choice options
       - The correct answer

- quizApp.js:
    - This is where the logic of the app being implemented
    - Handles showing questions, starting the timer, keeping track of your score, and showing results at the end
    - Uses event listeners to respond to your actions, like when you select an answer or hit "Next."


### A More Detail Overview of The Codebase Contained In Each File


### index.html


1) The html heading. Below is the heading format and process of linking the css, Font Awesome, and all of the js file

    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Quiz App Demo</title>

        <!-- CSS FILE -->
        <link rel="stylesheet" href="css/style.css">
        <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
        <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

        <!-- Add questions list -->
        <script src="js/questions.js" defer></script>

        <!-- Main logic of the app -->
        <script src="js/quizApp.js" defer></script>
    </head>
    ```

2) The html body. The body of this file is being used to create the components of dynamic user interactions. 

    - The Quiz Start Button: 

    ` <div class="start_btn"><button>Start Quiz</button></div>`

    - The Instruction box wrapper:

    ```
    <div class="info_box">
        <div class="info-title"><span>Some Rules of this Quiz</span></div>
        <div class="info-list">
            <div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
            <div class="info">2. Once you select your answer, it can't be undone.</div>
            <div class="info">3. You can't select any option once time goes off.</div>
            <div class="info">4. You can't exit from the Quiz while you're playing.</div>
            <div class="info">5. You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="buttons">
            <button class="quit">Exit Quiz</button>
            <button class="restart">Continue</button>
        </div>
    </div>
    ```

    - The Quiz Box (Where the question object is being displayed):

    ```
    <div class="quiz_box">
        <header>
            <div class="title">Demo Quiz App in JavaScript</div>
            <div class="timer">
                <div class="time_left_txt">Time Left</div>
                <div class="timer_sec">15</div>
            </div>
            <div class="time_line"></div>
        </header>
        <section>
            <div class="que_text">
                <!-- Insert questions from ./js/questions.js -->
            </div>
            <div class="option_list">
                <!-- Insert options to questions from ./js/questions.js -->
            </div>
        </section>
    </div>
    ```

    - The Footer 

    ```
    <footer>
        <div class="total_que">
            <!-- insert Question Count Number dynamically from JavaScript App logic -->
        </div>
        <button class="next_btn">Next Que</button>
    </footer>
    ```

    - The Result Box

    ```
    <div class="result_box">
        <div class="icon">
            <i class="fas fa-crown"></i>
        </div>
        <div class="complete_text">You've completed the Quiz!</div>
        <div class="score_text">
            <!-- insert dynamic user score as Result from JavaScript -->
        </div>
        <div class="buttons">
            <button class="restart">Replay Quiz</button>
            <button class="quit">Quit Quiz</button>
        </div>
    </div>
    ```

### index.css

1) Importing font from Google Fonts (on the top of the css file):
    `@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");`

2) You can open the CSS file in this repository since we only use one universal css file.

### question.js

1) Create an array of the question objects.
    - The attributes of the object are:
        - Question number
        - Questions
        - Options
        - Answers

    - Example of the object below: 
    ```
    {
        numb: 1,
        question: "What does HTML stand for?",
        answer: "Hyper Text Markup Language",
        options: [
        "Hyper Text Preprocessor",
        "Hyper Text Markup Language",
        "Hyper Text Multiple Language",
        "Hyper Tool Multi Language",
        ],
    },
    ```

### quizApp.js

1) Selecting all required elements from html document and store it as a global variable
    ```
    const start_btn = document.querySelector(".start_btn button");
    const info_box = document.querySelector(".info_box");
    const exit_btn = info_box.querySelector(".buttons .quit");
    const continue_btn = info_box.querySelector(".buttons .restart");
    const quiz_box = document.querySelector(".quiz_box");
    const result_box = document.querySelector(".result_box");
    const restart_quiz = result_box.querySelector(".buttons .restart");
    const quit_quiz = result_box.querySelector(".buttons .quit");
    const option_list = document.querySelector(".option_list");
    const time_line = document.querySelector("header .time_line");
    const timeText = document.querySelector(".timer .time_left_txt");
    const timeCount = document.querySelector(".timer .timer_sec");
    const next_btn = document.querySelector("footer .next_btn");
    const bottom_ques_counter = document.querySelector("footer .total_que");
    ```

2) Applying toggle functionality on some buttons to show info box:
    ```
    // if startQuiz button clicked
    start_btn.addEventListener("click", (e) => {
        info_box.classList.add("activeInfo"); //show info box
    });

    // if exitQuiz button clicked
    exit_btn.addEventListener("click", (e) => {
        info_box.classList.remove("activeInfo"); //hide info box
    });
    ```

    ```
    // if continueQuiz button clicked
    continue_btn.addEventListener("click", (e) => {
        info_box.classList.remove("activeInfo"); //hide info box
        quiz_box.classList.add("activeQuiz"); //show quiz box
        showQuetions(0); //calling showQestions function
        queCounter(1); //passing 1 parameter to queCounter
        startTimer(15); //calling startTimer function
        startTimerLine(0); //calling startTimerLine function
    });
    ```

    ```
    restart_quiz.addEventListener("click", (e) => {
        quiz_box.classList.add("activeQuiz"); //show quiz box
        result_box.classList.remove("activeResult"); //hide result box
        timeValue = 15;
        que_count = 0;
        que_numb = 1;
        userScore = 0;
        widthValue = 0;
        showQuetions(que_count); //calling showQestions function
        queCounter(que_numb); //passing que_numb value to queCounter
        clearInterval(counter); //clear counter
        clearInterval(counterLine); //clear counterLine
        startTimer(timeValue); //calling startTimer function
        startTimerLine(widthValue); //calling startTimerLine function
        timeText.textContent = "Time Left"; //change the text of timeText to Time Left
        next_btn.classList.remove("show"); //hide the next button
    });
    ```
    
3) Handling event listeners on quit quiz button when user done playing
    ```
    quit_quiz.addEventListener("click", (e) => {
        window.location.reload(); //reload the current window
    });
    ```

4) Handling event listeners on next button on the quiz info card
    ```
    // if quitQuiz button clicked
    quit_quiz.addEventListener("click", (e) => {
        window.location.reload(); //reload the current window
        });

        // if Next Question button is clicked
        next_btn.addEventListener("click", (e) => {
        //check if it does not exceed max questions
        if (que_count < questions.length - 1) {
            que_count++; //increment the que_count value
            que_numb++; //increment the que_numb value
            showQuetions(que_count); //calling showQestions function
            queCounter(que_numb); //passing que_numb value to queCounter
            clearInterval(counter); //clear counter
            clearInterval(counterLine); //clear counterLine
            startTimer(timeValue); //calling startTimer function
            startTimerLine(widthValue); //calling startTimerLine function
            timeText.textContent = "Time Left"; //change the timeText to Time Left
            next_btn.classList.remove("show"); //hide the next button
        } else {
            clearInterval(counter); //clear counter
            clearInterval(counterLine); //clear counterLine
            showResult(); //calling showResult function
        }
    });
    ```

5) Creating a function to show question from the array of object with an array parameter

    ```
    // If you have lesser or more number of options you need to change this code
    function showQuetions(index) {
        const que_text = document.querySelector(".que_text");

        //creating a new span and div tag for question and option and passing the value using array index
        // self exercise: re-write the following using backtick syntax for string in JS instead of concatenation operator
        let que_tag =
            "<span>" +
            questions[index].numb +
            ". " +
            questions[index].question +
            "</span>";
        let option_tag =
            '<div class="option"><span>' +
            questions[index].options[0] +
            "</span></div>" +
            '<div class="option"><span>' +
            questions[index].options[1] +
            "</span></div>" +
            '<div class="option"><span>' +
            questions[index].options[2] +
            "</span></div>" +
            '<div class="option"><span>' +
            questions[index].options[3] +
            "</span></div>";
        que_text.innerHTML = que_tag; //adding new (child) span tag inside que_tag
        option_list.innerHTML = option_tag; //adding new (child) div tag inside option_tag

        const option = option_list.querySelectorAll(".option");

        // set onclick attribute to all available options
        for (i = 0; i < option.length; i++) {
            option[i].setAttribute("onclick", "optionSelected(this)");
        }
    }
    ```

6) Implementation of the logic to handle right or wrong choice from the user
    ```
    // create new div tags for right or wrong tick icons
    let tickIconTag = '<div class="icon tick"><i class="fas fa-check"></i></div>';
    let crossIconTag = '<div class="icon cross"><i class="fas fa-times"></i></div>';

    //if user clicked on option
    function optionSelected(answer) {
        clearInterval(counter); //clear counter
        clearInterval(counterLine); //clear counterLine
        let userAns = answer.textContent; //getting user selected option
        let correcAns = questions[que_count].answer; //getting correct answer from array
        const allOptions = option_list.children.length; //getting all option items

        //if user selected option is equal to array's correct answer
        if (userAns == correcAns) {
            userScore += 1; //update total score value increment by 1
            answer.classList.add("correct"); //add green color to correct selected option
            answer.insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to correct selected option
            console.log("Correct Answer");
            console.log("Your correct answers = " + userScore);
        } else {
            answer.classList.add("incorrect"); //add red color to correct selected option
            answer.insertAdjacentHTML("beforeend", crossIconTag); //add cross icon to correct selected option
            console.log("Wrong Answer");

            for (i = 0; i < allOptions; i++) {
                if (option_list.children[i].textContent == correcAns) {
                    //if there is an option which is matched to an array answer
                    option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
                    option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
                    console.log("Auto selected correct answer.");
                }
            }
        }
        for (i = 0; i < allOptions; i++) {
            option_list.children[i].classList.add("disabled"); //once user select an option, disable all options
        }
        next_btn.classList.add("show"); //show the next button if user selected any option
    }
    ```

7) Implementation of showing the end result when the user finished going through all the questions in the question bank
    ```
    // display for result box based on user performance
    function showResult() {
        info_box.classList.remove("activeInfo"); //hide info box
        quiz_box.classList.remove("activeQuiz"); //hide quiz box
        result_box.classList.add("activeResult"); //show result box
        const scoreText = result_box.querySelector(".score_text");
        if (userScore > 3) {
            // if user scored more than 3
            //create a new span tag and pass the user score number and total question number
            let scoreTag =
            "<span>and congrats! , You got <p>" +
            userScore +
            "</p> out of <p>" +
            questions.length +
            "</p></span>";
            scoreText.innerHTML = scoreTag; //add new span tag inside score_Text
        } else if (userScore > 1) {
            // if user scored more than 1
            let scoreTag =
            "<span>and nice , You got <p>" +
            userScore +
            "</p> out of <p>" +
            questions.length +
            "</p></span>";
            scoreText.innerHTML = scoreTag;
        } else {
            // if user scored less than 1
            let scoreTag =
            "<span>and sorry , You got only <p>" +
            userScore +
            "</p> out of <p>" +
            questions.length +
            "</p></span>";
            scoreText.innerHTML = scoreTag;
        }
    }
    ```

8) Implementation of timer to set between each quiz question.
    ```
    function startTimer(time) {
    counter = setInterval(timer, 1000);
    function timer() {
        timeCount.textContent = time; //change the value of timeCount with time value
        time--; //decrement the time value
        if (time < 9) {
            //if timer is less than 9
            let addZero = timeCount.textContent;
            timeCount.textContent = "0" + addZero; //add a 0 before time value
            }
            if (time < 0) {
                //if timer is less than 0
                clearInterval(counter); //clear counter
                timeText.textContent = "Time Off"; //change the time text to time off
                const allOptions = option_list.children.length; //get all option items
                let correcAns = questions[que_count].answer; //get correct answer from array
                for (i = 0; i < allOptions; i++) {
                    if (option_list.children[i].textContent == correcAns) {
                    //if there is an option which is matched to an array answer
                    option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
                    option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
                    console.log("Time Off: Auto selected correct answer.");
                    }
                }
                for (i = 0; i < allOptions; i++) {
                    option_list.children[i].classList.add("disabled"); //once user select an option then disabled all options
                    }
                next_btn.classList.add("show"); //show the next button if user selected any option
            }
        }
    }
    ```

9) Implementation of a progress bar that reflects the timer function (another way of showing countdown time to create a better looking UI)

    ```
    // Shows a progress bar mirroring timer value left
    function startTimerLine(time) {
        counterLine = setInterval(timer, 29);
        function timer() {
            time += 1; //upgrading time value with 1
            time_line.style.width = time + "px"; //increasing width of time_line with px by time value
            if (time > 549) {
                //if time value is greater than 549
                clearInterval(counterLine); //clear counterLine
            }
        }
    }
    ```

10) Implementation of a que counter to help user identify which questions that they are on in respect to the total amount of questions

    ```
    function queCounter(index) {
        //creating a new span tag and passing the question number and total question
        let totalQueCounTag =
            "<span><p>" +
            index +
            "</p> of <p>" +
            questions.length +
            "</p> Questions</span>";
        bottom_ques_counter.innerHTML = totalQueCounTag; //adding new span tag inside bottom_ques_counter
    };
    ```