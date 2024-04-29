---
theme: seriph

background: https://images.unsplash.com/photo-1622737133809-d95047b9e673
title: TrustTech Talk
info: |
  ## TrustTech Talk
  A sharing session for trusty tech

  This talk will cover some basic knowledge to implement 3d object and
  animation on the web
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

## Exploring the World of Interactive 3D on the Web

Erick Hilda

---
layout: two-cols
layoutClass: gap-8
---

# Why Interactive 3D on the Web?

- 💡 **Contemporary Needs** - the increasing demand for more engaging and immersive user experiences.
-  📊 **Dynamic Data Visualization** - Using 3D scenes to visually convey product stories in a captivating way.
- 🎬 **Powerful Storytelling** - Using 3D scenes to visually convey product stories in a captivating way.
- 🚀 **Enhanced User Experience** - More intuitive navigation and immersive experiences.

::right::

<img v-click src="https://static.promediateknologi.id/crop/0x0:0x0/750x500/webp/photo/p1/10/2024/03/04/freepicture-2794707756.png" />

<div v-click>
  <p>some use case:</p>

  - [github internal dashboard](https://x.com/MaxPrilutskiy/status/1772871058783154245)
  - [kidsuper website](https://kidsuper.world/)
  - [MACintosh 40 Anniv](https://84-24.org/)
  - [NASA Eyes on Solar system](https://eyes.nasa.gov/apps/solar-system/#/home)
  - [MacBook Pro overview](https://www.apple.com/macbook-pro/)
</div>



---
transition: slide-up
---

# How to start?

<img v-click src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQJ-sIy44su239UkC1TtyEBkV7oX3Z8rCVzlsYa1RddoA&s" width="218"></img>


<div v-click>

  - Pros:
    - Fast and efficient 3D rendering on the client-side
    - Low-level control over the rendering pipeline
    - Support for advanced 3D features like shaders and textures

  - Cons:
    - Steep learning curve due to low-level API
    - Requires a modern browser with WebGL support
    - More verbose and less declarative than WebGL2
</div>

---
transition: slide-up
level: 2
---

# 

<img src="https://user-images.githubusercontent.com/5307958/38454395-eba34a8a-3a90-11e8-9c95-680a7aea037f.png" width="218"></img>

<div v-click>

  - Pros:
    - Large community and many resources available
    - Great for complex scenes and interactions
    - Providing a higher level API for common 3D tasks, making it easier to use than pure WebGL.

  - Cons:
    - Steep learning curve due to large API
    - Requires a modern browser with WebGL support
    - Not as efficient as WebGL2 for simple scenes
</div>

---
transition: slide-up
---

# 

## react-three-fiber ⚛️

<div v-click>

  - Pros:
    - Easy to learn and use
    - High-level declarative API
    - Reusable components
    - Good for 2D and 3D scenes
    - Good for beginners and advanced users
    - Good for performance-critical scenes

  - Cons:
    - Not as efficient as raw WebGL for complex scenes
    - Not as powerful as raw WebGL for advanced 3D features
    - Not as flexible as raw WebGL for low-level control
</div>
