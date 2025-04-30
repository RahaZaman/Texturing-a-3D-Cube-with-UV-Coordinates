# Lab 3: Texturing a 3D Cube with UV Coordinates

## Overview

This project demonstrates the use of UV coordinates to apply textures to a 3D cube in a WebGL environment. The goal is to map a texture containing images of a standard six-sided die onto the cube's faces. The project utilizes the `cuon-matrix-cse160` library for matrix operations and includes basic camera and rotation controls.

## Files

* `index.js`: The main entry point of the application. It initializes WebGL, sets up the shaders, creates the cube and camera, loads the textures, and starts the rendering loop.
* `Cube.js`: Defines the `Cube` class, responsible for creating the cube's geometry, setting up UV coordinates, loading textures, and rendering the cube.
* `Camera.js`: Defines the `Camera` class, which manages the view and projection matrices.
* `Controls.js`: Implements the `RotateControls` class, enabling interactive rotation of the cube using mouse drag events.
* `Context.js`: Provides a utility function to obtain the WebGL rendering context.
* `lib/`: Contains the `cuon-matrix.js`, `cuon-utils.js`, `webgl-debug.js`, and `webgl-utils.js` libraries for WebGL functionality and matrix operations.
* `img/`: Holds the texture images (`uvCoords.png` and `dice.png`).
* `styles.css`: Contains CSS styles for the HTML page.

## Setup

1.  **Dependencies:** Ensure you have a web browser that supports WebGL.
2.  **Libraries:** The project uses `cuon-matrix-cse160` (or `cuon-matrix.js`) for matrix operations and other utility functions. These libraries are included in the `lib/` directory.
3.  **Textures:** The `img/` directory contains `uvCoords.png` (for UV mapping reference) and `dice.png` (the texture to be applied to the cube).

## Code Highlights

###   `index.js`

* Imports necessary modules and assets.
* Defines vertex and fragment shaders.
* Initializes the WebGL context.
* Creates a `Camera` and a `Cube`.
* Loads textures onto the cube using `cube.setImage()`.
* Sets up rotation controls.
* Implements a rendering loop (`tick()`) that updates the scene and renders the cube.

###   `Cube.js`

* The `Cube` class stores vertex positions, UV coordinates, and texture handles.
* `setVertices()` defines the cube's geometry.
* `setUvs()` maps the texture onto the cube's faces.  **This is the core of the lab, where UV coordinates are carefully defined to align the die faces from `dice.png` onto the cube.**
* `setImage()` loads texture images and binds them to the cube.
* `calculateMatrix()` computes the model matrix for transformations.
* `render()` sends vertex data, UV coordinates, and matrices to the shaders for rendering.

###   `Camera.js`

* The `Camera` class calculates and stores the view and projection matrices.
* It updates the projection matrix when the window is resized to maintain correct aspect ratio.

## UV Mapping

The most important part of this project is the `setUvs()` function in `Cube.js`. It defines how the 2D texture is mapped onto the 3D cube.  The UV coordinates are carefully chosen to select specific regions of the `dice.png` texture, each containing a different face of the die.

## Running the Project

1.  Open the `index.html` file in a web browser that supports WebGL.
2.  You should see a textured cube that can be rotated by dragging the mouse.

## Lab 3 Specifics

This project was developed as part of a WebGL lab assignment focused on understanding and implementing UV coordinates for texturing. The lab involved:

* Mapping a texture containing die faces onto a cube.
* Manipulating UV coordinates to select specific portions of the texture for each cube face.
* Gaining familiarity with shaders and texture handling in WebGL.

## Notes

* The `cuon-matrix-cse160` (or `cuon-matrix.js`) library is used for matrix operations, simplifying the process of applying transformations to the cube.
* The `RotateControls` class provides basic user interaction for rotating the cube.
* The provided UV coordinates are specific to the layout of the `dice.png` texture. If a different texture is used, the UV coordinates will need to be adjusted.