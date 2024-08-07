(1) How do users interact with your executable? How to open and control the software you write (exe file)?
 
Open the software: Double-click the.exe file in the extracted folder to launch the emulator.

Keyboard operation:
1. Enter: Restore the cube to the initial state.
2. Rotation of each face: use the corresponding keys (such as R key to rotate the right side, U key to rotate the top, etc.). Hold down the Shift key and press the corresponding key to rotate counterclockwise.
3. Rotate the cube as a whole: Use the X, Y and Z keys for corresponding axial rotation.
4. Arrow keys: Move the cube's position.
   
Mouse operation:
1. Left-click the center block of each face: Rotate 90 degrees counterclockwise.
2. Right-click the center block of each face: Rotate 90 degrees clockwise.
3. Left press and drag: Rotate the viewing Angle.
   
Sidebar button control:
1. OpenGL Settings: You can turn on or off anti-aliasing, Gouraud coloring, light source and other options.
2. Magic Cube setting: Choose whether to use bitmap as the Rubik's cube pattern and draw the center block, edge block, corner block, etc.
3. Scaling Settings: Adjust the ratio of length, width and height of the cube.
4. Light setting: Adjust the direction of the light, pitch Angle, distance and other parameters.


(2) How does the program code work? How do classes and functions fit together, and who does what?

Main classes and functions
1. Main class:
• Responsibilities: Initialize the program, create Windows, enter the main loop.
• Function:
• main(): The entry point of the program, responsible for initializing the OpenGL environment, creating Windows, and starting the main loop.
• initialize(): Initializes OpenGL Settings such as anti-aliasing, light source, etc.
• reshape(width, height): deals with window size changes.
• display(): Render a Rubik's cube scene.
• keyboard(key, x, y): Handles keyboard input.
• mouse(button, state, x, y): handles mouse input.
motion(x, y): handles mouse drag.
2. MagicCube class:
• Responsibilities: Represent and manage the cube's status and operation.
• Member variables:
• faces: Stores the status of each side of the cube.
• Function:
• reset(): restores the cube to its initial state.
• rotate_face(face, direction): Rotates the specified face(clockwise or counterclockwise).
• rotate_cube(axis, direction): Rotates the entire Rubik's cube along the specified axis.
apply_formula(formula): Apply the formula and rotate the Rubik's cube step by step.
3. Renderer class:
• Responsibilities: Responsible for the drawing of Rubik's cube.
• Member variables:
• cube: An instance of MagicCube that provides the state of the cube.
• Function:
• draw(): Draw the entire Rubik's cube.
• draw_face(face): Draws a face of the Rubik's cube.
• apply_transformations(): Applies transformations, such as viewing angles and scaling.
4. FormulaPlayer class:
• Responsibilities: Manage and play Rubik's Cube formula.
• Member variables:
• cube: An instance of MagicCube that provides the state of the cube.
• formula: Stores the current formula.
• playing: Indicates whether a formula is being played.
• Function:
• load_formula(file_path): Loads formulas from a file.
• start_playing(): Start playing formula.
• stop_playing(): Stops the playing formula.
• update(): To update the formula playback status, go to the next step.
5. Utility:
• Responsibilities: Provide common utility functions.
• Function:
• parse_formula(formula_str): parses formula strings and converts them into internal step representations.
• load_texture(file_path): Loads the texture image.

Class and function collaboration
1. Initialization:
• The main() function first calls initialize() to set OpenGL parameters, then creates the MagicCube and Renderer instances.
• main() enters the main loop, binding the reshape(), display(), keyboard(), mouse() and other callback functions.
2. User input:
keyboard() and mouse() callbacks respond to user input, such as keyboard rotations and mouse actions.
• When the user presses the appropriate key, the keyboard() function calls MagicCube's rotate_face() or rotate_cube() methods to update the cube's state.
3. Render:
Each time the window is refreshed, the display() function calls Renderer's draw() method to draw the current state of the cube.
• Renderer draws each face and block according to the state of the MagicCube.
4. Playing formula:
• After the user loads the formula file, the load_formula() method of FormulaPlayer reads and parses the file contents.
• When the play key is pressed, the start_playing() method of FormulaPlayer begins to play the formula.
• In each iteration of the main loop, the update() method of FormulaPlayer is called, executing the steps in the formula in order, calling the methods of MagicCube to update the state.

(3)What makes your program special and how does it compare to other programs?

1. Keyboard control: Supports a variety of rotation operations (R, U, F, L, D, B keys and their counterclockwise versions).
2. Mouse control: Click and drag to adjust the Angle of view and rotate the surface.
3. Sidebar Settings: Quickly adjust render modes, lighting effects, and texture applications.
4. Anti-aliasing and Gouraud shading: provides high quality visual effects.
5. Real-time lighting adjustment: Change the direction, intensity and concentration of the light.

Special point:
1. Efficient OpenGL rendering ensures smooth and real-time operation.
2. Customize textures and multiple rendering modes to enhance cube visualizations.
3. Educational function, through the formula play show Rubik's cube operation process, convenient learning and teaching.


VIDEO LINK:https://youtu.be/L_GJH9KO4jM

