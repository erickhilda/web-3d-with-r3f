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

## 

<img v-click src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQJ-sIy44su239UkC1TtyEBkV7oX3Z8rCVzlsYa1RddoA&s" width="218"></img>


<div v-click>

- Natively support by "modern" browser
- Gain overall control over the rendering pipeline
- Steep learning curve due to low-level API

learning resources:

- [Creating 3D objects using WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Tutorial/Creating_3D_objects_using_WebGL)
</div>


---
transition: slide-up
level: 2
---

<img src="https://user-images.githubusercontent.com/5307958/38454395-eba34a8a-3a90-11e8-9c95-680a7aea037f.png" width="218"></img>

<div v-click>

- Large community and many resources available
- Providing a higher level API for common 3D tasks, making it easier to use than pure WebGL
- Kinda less steep learning curve than barebone WebGL
- Great for complex scenes and interactions

learning resources:
- [Three.js Docs.](https://threejs.org/)
- [Three.js Journey by Bruno Simon](https://threejs-journey.com/)
</div>

---
transition: slide-up
layout: two-cols
---

# 

## react-three-fiber ⚛️

<div v-click>

- Less friction when integrate into modern tools
- Provide threejs abstarction as components
- Have many utility tools around react environment
- if you coming from react, it is easier to learn

learning resources:
- [Three.js Docs.](https://threejs.org/)
- [r3f Docs.](https://docs.pmnd.rs/react-three-fiber/getting-started/introduction)
</div>

::right::

````md magic-move
```ts

```

```ts {*|3|4-6|7-8|*}
// example of using threejs to create object
...
const geometry = new THREE.BoxGeometry(1, 1, 1); 
const material = new THREE.MeshBasicMaterial({
    color: 0x00ff00
}); 
const cube = new THREE.Mesh(geometry, material); 
scene.add( cube );
...
```

```ts {*|4|5|*}
// how it will be as r3f
...
<mesh>
    <boxGeometry args={[1, 1, 1]} />
    <meshBasicMaterial color="hotpink" />
</mesh>
```

```ts
// how it will be as r3f
...
function Box(props: JSX.IntrinsicElements['mesh']) {
    const mesh = useRef<Mesh>(null!)
    const [hovered, setHover] = useState(false)
    const [active, setActive] = useState(false)

    return (
        <mesh
            ref={mesh}
            scale={active ? 1.5 : 1}
            onClick={() => setActive(!active)}
            onPointerOver={() => setHover(true)}
            onPointerOut={() => setHover(false)}
            {...props}
        >
            <boxGeometry args={[1, 1, 1]} />
            <meshBasicMaterial 
                color={hovered ? 'hotpink' : 'orange'}
            />
        </mesh>
    )
}
```
````

---
transition: slide-up
layout: two-cols
layoutClass: gap-8
---

# Geometry

<figure v-click>
  <img src="https://www.mathsisfun.com/geometry/images/vertex.svg" width="128"></img>
  <figcaption>Vertices</figcaption>
</figure>

<figure v-click>
  <img src="https://www.mathsisfun.com/geometry/images/edges.svg" width="96"></img>
  <figcaption>Edges</figcaption>
</figure>

<figure v-click>
  <img src="https://www.mathsisfun.com/geometry/images/faces.svg" width="96"></img>
  <figcaption>Faces</figcaption>
</figure>

::right::

````md magic-move
```ts


```

```ts
import { Mesh } from 'three'
import { useFrame } from '@react-three/fiber'
import { useRef, useState } from 'react'

function Box(props: JSX.IntrinsicElements['mesh']) {
  const mesh = useRef<Mesh>(null!)
  const [hovered, setHover] = useState(false)
  const [active, setActive] = useState(false)
  useFrame(() => (mesh.current.rotation.x = mesh.current.rotation.y += 0.01))

  return (
    <mesh
      {...props}
      ref={mesh}
      scale={active ? 1.5 : 1}
      onClick={() => setActive(!active)}
      onPointerOver={() => setHover(true)}
      onPointerOut={() => setHover(false)}
    >
      <boxGeometry args={[1, 1, 1]} />
      <meshStandardMaterial color={hovered ? 'hotpink' : 'orange'} wireframe />
    </mesh>
  )
}

export default Box
```
````
