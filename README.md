Simple old school battle ship game in visual studio using C# programming language.
In this game you will create an AI player where you can play against them to win your sea battles.  Custom-made background image we will use in our game. This has the positions for the player and the enemy. It also has the player move and enemy move tabs on the top.

Project Steps

* Complete the simple battle ship game in visual studio
* Use custom background on the windows form
* AI make decisions in the game
* Player controls their ships from list of moves
* Keep track of AI movements
* Using windows GUI to create a game
* Using LIST arrays in C#
* Using LOOPs in C#
* Searching indexes of the list arrays and matching them to integers
* Using System Diagnostics show system debug information in the outputs window
* Using multiple timers and controlling them dynamically
* Showing customised win, lose and draw message box

EnemyPlayTimerEvent;

This event will be triggered by the enemy play timer. We want this timer to select a random location from the play positions array and attack it. If that position is where the player hid their ships then it will sink or it will show the miss icon. That’s the overall idea behind this event. 

This function is also responsible for checking the rounds and the player and enemy scores. We also have placed several if statements in the bottom of the function to check if we have won, drew or lost the game against the CPU. 

AttackButtonEvent;

Attack button event is triggered when the attack button is clicked by the player. We are going to put this whole thing inside an if statement. Logic behind this is when the player selects an option from the drop down menu we can attack that position but if the drop down list position is empty then we want to remind the player to select a location from the list. We are using the lists find index function to search for the button location selected from the list.

There is a if statement in this function the logic is when the player attacks a position we need to check if that attack position has a tag of enemyship if it does then we change the icon to the fire image we imported earlier, disable that button, add 1 to the player score and we will start the enemy play timer.If that tag doesn’t match the position the player attacked then we will disable that button and we will give it a miss icon as a background and then we will star the enemy play timer.

PlayerPositionButtonsEvent;

This function will run each time the player will click on their own button. In this function we have two IF statements. The first IF statement is checking is the totalShips integer has a greater value than 0 meaning it has more than 1 then we allow the instructions inside to run. First it will check which button was clicked and store it in the local variable called button. Then we will disable that button and give it a tag of playership. 

Tags are useful to identify an object when we have multiple objects in the program. In this if statement when the button is clicked we will give it a background colour of blue so its easier to identify it and then we will reduce 1 from the total ships integer. The logic here is we want the player to only be able to select 3 buttons so we gave total ships integer a value of 3, each time the player picks a button total ships integer reduces by 1 and when it gets to 0 it will fire up the second if statement.

The second if statement is checking if the total ships 0 then we enable the attack button, give it a background colour RED. The help text which shows that player needs to select 3 buttons now will be moved to the top and will say 2) Now Pick a attack position from the drop down. 

enemyLocationPicker;

This event is responsible for the CPU to pick its three positions from the array of buttons. This event will be triggered when the form is loaded. 

In this event we will use the random number generator. Pick a random button from the array of enemy position buttons when it will pick a button it will add a tag called enemyship to that specific button and it will reduce the total enemy by 1. This is the same logic we used when we wanted that player to pick three positions. 

Lastly if the total enemy is below one then we can stop the timer and we are ready to play.

using System.Diagnostics; 
This line will allow us to use the System Diagnostics class from C#, we will be asking our AI to pick its position on the array of buttons,but we will not know which buttons it picked to test out the game mechanics. C# has just the thing for us we can call the diagnostics class and use the debug.log to output the moves AI picked in the outputs window and test the game. It’s an useful tool for programmers and I recommend you use it in your big projects that can save lots of time and energy.

List<Button> ;
playerPosition and enemyPosition are both dynamic array of buttons. Notice we mention <Button> in the list we can call anything we want to make an array but for this game we have lots of buttons and we need a way to organise and use them efficiently. This is why we are using the LIST data type for the buttons.

Random rand = new Random(); 
This is a Random number generator class build into C#, we will be using this to allow the AI to randomly pick 3 positions for the enemyPosition array.

int totalShips;
is for the user. By using this golabl int variable we will be able to allow the user to only pick 3 buttons from the playerPosition array. The same logic will be used for the int totalenemy.

int rounds, int playerScore and enemyScore;
are to keep track of the rounds played and how much the player or the enemy scored in the game.


