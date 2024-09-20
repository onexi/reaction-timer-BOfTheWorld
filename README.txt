[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/e__G6ZpK)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=15891440)

Starter Code for Reaction Timer 
Run npm install to install all dependencies 
The above uses package.json to build the project
Note .gitignore is set to ignore node_modules

***************** ABOUT THE APPLICATION ***********************
Reaction Timer APP is a an application to test and record users' reaction time with timestamp on when it was submitted.

The app has the following features:
1. User Name Input - user can input his/her name to record the reaction time
2. Reaction Time Button - the button which changes color and text display depending on the state/phase of the game
3. Unlimited trial - User has unlimited trial until he/she submits his record
4. Ranked List - a ranked list of all the users who tried the app
5. Cheating prevention - If a user clicks 5 consecutive errors (clicking before the button turns green), the user will be disabled for 20 seconds.

***************** REQUIREMENTS BEFORE SUMITTING ENTRY ***********************
Requirements to submit entry:
    1. There should be a Name entry in the inputbox
    2. You should play and have reaction Time

*********** INSTRUCTION ON HOW TO PLAY/USE THE APP *********
Instructions:
    1. Click Start Game button
    2. Wait for the button to turn to green and displays "Click Now!" before you click. This will capture your reaction time
    3. Make sure you have name
    4. Click submit if you are happy with your performance and see where you rank based on the previous users who played the game.

***************** CHEATING PREVENTION ***********************
This app has a cheating prevention mechanism. If a user clicks 5 consecutive times before the Green Button, the user will be banned to use the app for 20 seconds.

***************** CODE DETAILS ***********************
-------- HTML --------
<style> Provides addition formatting for the buttons to be consistent in width and to put it in the middle of the screen
<head> Includes https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css for formatting
<body>
    <h1> For the Label of the APP
    <input> For the Name.
    <button> Starting the button in blue with text "Start Game". When clicked, code will run scipt function startTheTime.
    <p> Shows your Reaction Time and comment depending on the event
    <h4> Below this label will show the Ranked Submitted Users with their Reaction Time and Timestamp of their entry
    <script>
        First part is declaration of constants
        Script makes the Result comments Italic
        function submitEvent() - This handles the submit button. The system checks first if there is a Username and if there is a reaction time
            function then send data to the server in JSON format
            function then handles the response from the server
            function then prepares the data for creation of new and updated list to be displayed in <ul>. This includes sorting the data in ascending manner based on reaction time to show the ranking of the users
            function then clears the reactionTime, reset the button to be able to play again.
            include a catch error

        function startTheTime() - This handles the event once button is clicked to start/restart game
            function then changes the color of the button and test to ask user to wait for the button to change to green before clicking
            function then creates a random delay between 1 to 20 seconds
            function then enables a button listener to handle the button event
            function also checks if user prematurely clicks the button for 5 consecutive times. function then triggers handleError function
            function then handles the delay then changes the button to green after the delay. a varibale isGreen is the set to true. Starttime is then saved for reaction time calculation
            function has handling if user did not press the button after 1minute it changed to green

        function handleButtonClick() - This handles the clicked button event upon the start of the game.
            functionc checks if variable isGreen is true. If true, code will calculate the Reaction time by subtracting the current time minus the start time the button turned green
            function then reset the variable isGreen for the next run of the game. Then gives the option to the user to try again if the user is not happy with his reaction time.
            if variable isGreen is false, button will change to red to make the tell the user he/she clicked before the button turned to green. function also will increment the errorCounter

        function handleError() - This handles the even if the user clicked the button for 5 consecutive times before it turns green.
            function then disables the button for 20 seconds as a penalty to the user.
            after the 20 secs ban, function then resets the errorCounter.

-------- SERVER JS --------
First part of the code is for declarations
    Declaration of port included
    Declaration of formData array for the data
    App also allows parsing of JSON since data from HTML will be passed to the server in JSON format.
    JS file serve the index.html
    JS handles the data from HTML and add the data in the formData array
    JS runs the server to the Port declared.