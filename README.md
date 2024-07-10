# FallingSandApplesoftBasic
This is a very simple Falling Sand Simulation written in Applesoft Basic.
## 1. Variable Initialization
In Applesoft Basic, only the first two letters of a variable are actually saved. If you initiate the variables "CurserPositionX" and "CurserPositionY", they will be treated as the same variable called "Cu". To avoid this issue, I use short variable names, as it is very hard to spot this error when troubleshooting.

- hgr: Initializes the high-resolution graphics mode.
- cx and cy: Current position of the cursor.
- n: Number of sand particles.
- dim p(256,1): Defines an array p to hold the positions of up to 256 sand particles.
- md, ml, mr: Flags indicating possible movement directions (down, left, right).
- dl: Delay loop counter.
- x: Limits the checks to particles that haven't reached the ground.
- fi, f: Variables to keep track of the image buffer.
- ts: Size of each tile in the grid.
- gosub 1000: Calls subroutine 1000 to create the first sand particle.

## 2. Main Loop
The main loop calls the logic function, the key listener, the wait function, and the draw function, before looping over itself until the program is terminated.

## 3. Creating a New Instance
Sets the current cursor position as the position of the new particle and increments n.

## 4. Sand Particle Logic
Loops over every particle to check if the bottom, bottom-left, or bottom-right cells are empty. Depending on which ones are free, it will move the particle accordingly, prioritizing the middle over everything and left over right.

## 5. Key Listener and Event Manager
Assigns the current key ID to variable k and then checks k for arrow keys and the space bar to perform the corresponding actions. The space bar calls the function to add a new particle at the cursor position, and the arrow keys move the cursor.

## 6. Crude Wait Function
Since Applesoft Basic doesn't support multiple threads or have an integrated timer, the most common way to create a delay is to loop over nothing, using a variable that represents the duration of the wait. This method is inaccurate, as the desired value has to be estimated through trial and error, and the duration won't be consistent because it is based on computing steps rather than actual time.

## 7. Draw Function
First, it changes the page it is plotting to and then clears it. Afterwards, it loops over the array and plots a square with the tile size as its edge length at the position of the particle, using a predefined color. The cursor is then plotted with two orthogonal lines creating a cross with the same cell size and a different predefined color. After the plotting is done, it will change the currently displayed page to the newly plotted page.
