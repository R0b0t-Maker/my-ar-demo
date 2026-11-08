# My AR Demo: Marker-Based WebAR with A-Frame and AR.js

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![A-Frame](https://img.shields.io/badge/A--Frame-1.2.0-EF2D5E?logo=aframe&logoColor=white)](https://aframe.io/)
[![AR.js](https://img.shields.io/badge/AR.js-marker_tracking-blue)](https://github.com/AR-js-org/AR.js)
[![GitHub Pages](https://img.shields.io/badge/demo-GitHub_Pages-222222?logo=githubpages&logoColor=white)](https://r0b0t-maker.github.io/my-ar-demo/)

A minimal browser-based augmented reality demo. Point a phone camera at the standard "Hiro" marker and a 3D model (`model.glb`) appears on top of it, rendered with A-Frame and tracked with AR.js. There is no build step and no app to install.

Live demo: https://r0b0t-maker.github.io/my-ar-demo/

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [How It Works](#how-it-works)
- [License](#license)
- [Contact / About](#contact--about)

## Overview
A single static page that demonstrates marker-based WebAR.
1. **A-Frame scene**: an `<a-scene>` with the `arjs` component and a camera entity.
2. **Marker tracking**: AR.js detects the preset Hiro marker in the camera feed.
3. **3D content**: a glTF binary model anchored to the marker.

It runs in any modern mobile browser that allows camera access over HTTPS.

## Key Features
- **No install**: runs straight from GitHub Pages in the browser.
- **Marker-based tracking**: uses AR.js's built-in Hiro marker preset.
- **glTF model**: loads `model.glb` with A-Frame's `gltf-model` component.
- **Single file**: all logic is declarative HTML in `index.html`.

## Installation
Clone the repository:
```bash
git clone https://github.com/R0b0t-Maker/my-ar-demo.git
cd my-ar-demo
```
There are no dependencies to install. A-Frame 1.2.0 and AR.js are loaded from CDNs at runtime.

## Usage
Serve the folder over HTTP (the camera needs a secure context, so use `localhost` or HTTPS):
```bash
python -m http.server 8000
```
Open http://localhost:8000 (or the GitHub Pages URL on a phone), allow camera access, and point the camera at a printed or on-screen [Hiro marker](https://raw.githubusercontent.com/AR-js-org/AR.js/master/data/images/hiro.png).

## Code Structure
- **`index.html`**: the A-Frame scene, AR.js setup, marker and model entity.
- **`model.glb`**: the 3D model shown on the marker (about 19 MB).
- **`README.md`**: this file.

## How It Works
The page loads `aframe.min.js` (1.2.0) and `aframe-ar.min.js` (AR.js). Inside `<a-scene embedded arjs>`, an `<a-marker preset="hiro">` holds an `<a-entity gltf-model="model.glb">`, so the model is drawn relative to the marker's pose each frame. Position, rotation and scale attributes on the entity control how the model sits on the marker.

<!-- TODO: index.html currently contains two overlapping copies of the scene (a second full <!DOCTYPE html> document is pasted inside the first). Keep one copy and pick one scale (0.3 or 0.01). -->
<!-- TODO: pin the AR.js CDN URL to a release tag instead of the default branch. -->

## License
<!-- TODO: add a LICENSE file -->
No licence file yet. The origin and licence of `model.glb` are not stated in the repository.

## Contact / About
Developed by Rasoul Sadeghian.
