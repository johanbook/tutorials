# Three.js

This document describes the JavaScript library `three.js`, however, some
concepts may be more general.

## Basic concepts

- **Renderer** Responsible for rendering a 2d image to a HTML canvas.
- **Camera** The camera determines what should be rendered.
- **Scene** Defines the root of the scenegraph.
- **Geometry** Describes the geometry of an object using vertexes.
- **Material** Describes the surface of an object.
- **Mesh** Is a geometry with its corresponding material. Mesh holds
  position,rotation etc meaning one can have multiple different meshes using the
  same material and geometry in different locations.
- **Light** A light source.

## Frustrum

A frustum is the view area for a camera, typically a pyramid with the top cut
off.
