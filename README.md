# Towers_Of_Hanoi_Game
Computer organization project: Built the digital version of the Towers of Hanoi game on a ARMv7 DE1-SoC simulator, CPUlator.

Check out our [presentation](https://youtu.be/kFwgeKDJygw):

[![Demo](https://img.youtube.com/vi/kFwgeKDJygw/0.jpg)](https://www.youtube.com/watch?v=kFwgeKDJygw)


2021 - Team Course Project

Teammate: Nicholas Heeralal

Tools used for game development: C Programming Language, ARM Processor, CPUlator


***1.0 Description***

There are three towers, represented in white. There are three to five disks, represented in colorful different sized rectangles, depending on the level of the game. The pink arrow points at the tower and selects the upper disk on the tower based on the user input  (Section 3). The user can play the game using the keyboard and pressing on certain switches (Section 3).

![Screen Shot 2021-07-20 at 12 15 34 PM](https://user-images.githubusercontent.com/67078190/126359180-aec3b95b-4ddb-4b62-b513-d2190704f4c4.png)




***2.0 Goal and Rules***

GOAL: Move all the disks over to Tower C (right-most).

- Only one disk may be moved at a time.
- Each move consists of taking the upper disk from one of the towers and placing it on top of another tower.
- No disk may be placed on top of a disk that is smaller than it.




***3.0 How To Play***

In the beginning, the introduction page is seen. To play, follow the next steps.

**3.1 Pick a Level**

There are three levels in this game, where the increase in the number of disks in the game increased the difficulty.
Level 1: 3 disks,	Level 2: 4 disks,	Level 3: 5 disks
- Press SW-0 to select Level 1. When the respective LED is turned on, un-press SW-0.
- Press SW-1 to select Level 2. When the respective LED is turned on, un-press SW-1.
- Press SW-2 to select Level 3. When the respective LED is turned on, un-press SW-2.

![Screen Shot 2021-07-20 at 12 16 29 PM](https://user-images.githubusercontent.com/67078190/126359320-420bd0c0-ee97-4f99-822d-b40218130433.png)
                         
Figures show Level 1 is selected.

NOTE: Please ensure you unpressed the switch after selecting your desired mode of play.

Then, the game will be displayed.
The minimum possible score you can make is displayed on the leftmost HEX Displays (HEX5 and HEX4) and your current score displayed on the rightmost HEXES (HEX 1 and HEX0).

**3.2 Move the Disks**

1. After clicking and releasing your switch of choice to determine mode, use your mouse to click and press the key into the first PS/2 Keyboard input device.
When the up arrow (or W) is pressed, the disk gets selected and raised above the tower.

2. When the down arrow (or S) is pressed, the disk gets dropped to the tower below, if the move is valid (see Section 4.2 for an invalid move).

3. The left and right arrow keys (or the A and D) are used to move and select a tower, to later pick up or drop off the upper disk, as described above.

4. At any point in gameplay, if you want to restart the game to select an easier/harder game mode, or simply just want to do something else, pressing the R key would take you back to the introduction page to pick a level (Section 3.1) or see the auto-solver (Section 4.3).

**3.3 End of Game**

After completing the task, regardless of the number of moves it takes, the “You Win!” page is shown. To try playing again to perform a better result, play with a different level, or see the fastest method to win through the auto-solver, press key R to reset. Then, choose your level (Section 3.1) or the auto-solver (Section 4.3).

***4.0 Features***

The following features assist the player in playing the game.

**4.1 Display of the Number of Moves**

HEX4 and HEX5 display the minimum number of moves it takes to complete the game, where a higher level has a greater number of moves to complete the game.

HEX1 and HEX0 display the number of moves played by the player throughout the game, where the number displayed gets incremented by one after each valid move.

![Screen Shot 2021-07-20 at 12 20 44 PM](https://user-images.githubusercontent.com/67078190/126359931-3e875b52-1075-479d-852c-e0f332907781.png)


**4.2 Warning of Invalid Moves**

A warning of “Invalid Move” is displayed, if a player tries to place a larger disk on top of a smaller disk, or lift another disk while the arrow is holding one. 

NOTE: This does not count as a move.

![Screen Shot 2021-07-20 at 12 21 00 PM](https://user-images.githubusercontent.com/67078190/126359977-b1ce9875-eb9c-42f1-91c7-6a8da365804a.png)


**4.3 Auto-Solver**

The auto-solver visually and descriptively shows the steps to be taken to complete the level with the minimum number of steps. The visual is shown through the animation and the description of moves is shown in the Messages (terminal).
- Press SW-7 to select the Auto-Solver for Level 1. When the respective LED is turned on, un-press SW-7.
- Press SW-8 to select the Auto-Solver for Level 2. When the respective LED is turned on, un-press SW-8.
- Press SW-9 to select the Auto-Solver for Level 3. When the respective LED is turned on, un-press SW-9. 

Throughout the animation, the HEX4 and HEX5 display the minimum number of moves it takes to complete the game while HEX1 and HEX0 display the step number of the move. At the end of each level completed, a “Level Complete” page is shown.

NOTE: The R key to get back to the introduction page is disabled when the auto-solver is being displayed. Furthermore, you will return to the introduction page after seeing the hint.

***5.0 Source Code Information***

The primary data structure utilized was a linked list. Each tower is represented by a list. If a tower’s head node is NULL, it is empty. At the beginning of the gameplay, the first tower is initialized with the number of disks chosen with the largest disk number at the beginning of the list. To move a disk to another tower, the next tower must either be null (empty) or at the end of that tower’s list (the topmost disk), that disk must be larger than the one you want to play. To aid with these moves; there is a data structure that represents the Arrow to store information of the tower is currently over and if it is holding a disk or not. A win is detected if the third tower has the number of nodes (disks) placed onto it. 

A summary of the I/O devices used is as follows:
- Switches - to select the mode of the program.
- LEDs - to display the switch-mode selected.
- HEX Displays - to display the minimum possible score and user’s current score.
- PS/2 Keyboard - to input user moves.
- VGA pixel buffer - to display the gameplay.
- Character Buffer - to display the warning messages.
- ARM A9 Private Timer - used to achieve delay effects in the auto-solver.

