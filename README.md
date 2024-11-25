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

1) The HTML heading. Below is the heading format of index.html file as well as linking the css, Font Awesome, and all of the js file

    - ```
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
    


    