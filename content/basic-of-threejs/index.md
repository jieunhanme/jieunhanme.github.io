---
emoji: ๐งโโ๏ธ
title: Three.js์ ๊ธฐ์ด๋ฅผ ์์๋ณด์!
date: '2022-03-30 17:30:00'
author: ํ์ง์
tags: ๋ธ๋ก๊ทธ threejs 3d WebGL
categories: Threejs featured
---

<a href="https://threejs.org/" target="_blank" >
<img src="./basic-of-threejs-01.png" alt="threejs.org"/>
</a>

---

์ต๊ทผ ์คํฌ๋กค ์ธํฐ๋ ์ ์น ์ฌ์ดํธ ๊ณต๋ถ๋ฅผ ํ๋ฉด์, ๋ ํ๋ คํ๊ณ  ๋ฉ์ง 3D ์น์ฌ์ดํธ ๊ตฌํ์ ์์ฐ์ค๋  ๊ด์ฌ์ด ์๊ฒผ๋ค.
์ฌ์ค ๋๋ ์ด์ ์ Threejs๋ฅผ ์ด์ง ๊ณต๋ถํ๋ค๊ฐ ์ข์ ํ ๊ฒฝํ์ด ์๋๋ฐ... ๋๋ฌด ๋งค๋ ฅ์ ์ธ ํ๋ ์์ํฌ์ง๋ง, ์ฝ๊ฒ ์ ํ  ์ ์๋ ์ค๋ช์ ๋๋ถ๋ถ ์์ด๋ก ๋์ด์์ด Canvas๋ ๋ฏธ์ํ ๋ด๊ฒ๋ ๋๋ฌด ์ด๋ ค์ ์๋ค.

![threejs๋ก ๋ง๋ค์๋ ๊ฒฐ๊ณผ๋ฌผ](./basic-of-threejs-02.png)

<p class="img-caption" style="margin: -30px 10px 0 10px;">๊ทธ ๋น์ ๋ง๋ค์๋ 3D ์ค๋ธ์ ํธ... ์ ๋ก๋ฅผ ๋ฐ๋ผ ๋ฌ๋ฆฌ๋ ๋ง์ ํํํ๊ณ  ์ถ์์ง๋ง ๊ฐ๋ ์ดํด๋ฅผ ์ ๋๋ก ํ์ง ๋ชปํด ๊ฒฐ๊ตญ ํฌ๊ธฐํ๋ค.๊ฐ๋์ ์ ๋๋ก ์ตํ์ง ์์ ์ํ๋ก REACT๋ก ๊ฐ๋ฐํ๊ฒ๋ ํ๋ชซ ํ๋ค.</p>
<br />

ํ์ง๋ง 3D์น ์ฌ์ดํธ๋ฅผ ๊ตฌํํ๊ณ ํ ๋์ ์์ฌ์ด ๋๋ฅผ ๋ค์ Threejs์์ผ๋ก ์ด๋์๋ค. ์ด๋ฒ์๋ ๊ผญ ์ข์ ์ฑ๊ณผ๋ฅผ ์ด๋ฃจ๊ธธ ๋ฐ๋ผ๋ฉฐ ๋ค์ ๊ธฐ์ด๋ถํฐ ๊ณต๋ถ๋ฅผ ์์ํด๋ณด์!!

๊ฐ๋ฐ ํ๊ฒฝ์ webpack + module threejs๋ฅผ ๋ฐํ์ผ๋ก ์งํํ์ต๋๋ค.

---

## ๐ Three.js๋?

**Three.js**๋ ์นํ์ด์ง์ 3D๊ฐ์ฒด๋ฅผ ์ฝ๊ฒ ๋ ๋๋งํ๋๋ก ๋์์ฃผ๋ ์๋ฐ์คํฌ๋ฆฝํธ 3D ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ด๋ค.
Three.js๋ 3D๊ฐ์ฒด๋ฅผ ๋ ๋๋งํ๋๋ฐ `WebGL`์ ์ฌ์ฉํฉ๋๋ค.

> **WebGL(web Graphics Library)** <br /> ์ , ์ฌ, ์ผ๊ฐํ๋ง ๊ทธ๋ฆฌ๋ ์์ฃผ ๋จ์ํ ์๋ฐ์คํฌ๋ฆฝํธ

WebGL๋ก ์์ํ๋ ค๋ฉด ์์๋์ด ๋ง์์ง๊ณ  ์ฝ๋ ์์ฒด๋ ๋ณต์กํด์ง ์ ๋ฐ์ ์๋๋ฐ...
์ด๋ฐ ๋จ์ ์ ๋ณด์ํ๊ณ ์ 3D ๊ฐ์ฒด๋ฅผ ์กฐ๊ธ ๋ ํธํ๊ณ  ํจ์จ์ ์ผ๋ก ์งค ์ ์๊ฒ ๋์์ ์ฃผ๋ `Three.js`, `Babylon.js`์ ๊ฐ์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ฌ์ฉํ๋ค๊ณ  ํฉ๋๋ค.

## ๐ Threejs์ ๊ตฌ์ฑ์์

![structure of threejs](./basic-of-threejs-03.png)

<p class="img-caption" style="margin: -15px 10px 0 10px;">
three.js์์ ์ ๊ณตํ๋ ๋ค์ด์ด๊ทธ๋จ
</p>
<br />

threejs๋ก ํํ์ ํ๋ ค๋ฉด Renderer, Scene ๊ทธ๋ฆฌ๊ณ  Camera๊ฐ ๋ฐ๋์ ์์ด์ผํฉ๋๋ค.
<br />
๊ฐ๊ฐ์ ์์๊ฐ ์ด๋ค ์ญํ ์ ํ๋์ง ํ๋์ฉ ์์๋ด์๋ค ๐ง

<br />

### ๐ฌ Renderer

Renderer๋ Three.js์ ํต์ฌ ๊ฐ์ฒด๋ก `Scene`๊ณผ `Camera`๊ฐ์ฒด๋ฅผ ๋๊ฒจ ๋ฐ์ ์นด๋ฉ๋ผ์ ์ ๋์ฒด ์ 3D์ฌ์ ์ผ๋ถ๋ฅผ ํ๋ฉด(2์ฐจ์) ์ด๋ฏธ์ง๋ก ๋ ๋๋งํฉ๋๋ค. ์ฝ๊ฒ, Camera๊ฐ ๋ด๊ณ ์๋ Scene๋ฅผ ํ๋ฉด์ ์ถ๋ ฅํด์ฃผ๋ ๊ฐ์ฒด๋ผ๊ณ  ์๊ฐํ์๋ฉด ๋ฉ๋๋ค.
<br />
Renderer๋ฅผ ์์ฑํ๋ ๋ฐฉ๋ฒ์ ์๋์ ๊ฐ์ด ๋๊ฐ์ง๊ฐ ์์ต๋๋ค.

1. javascript์์ renderer๋ฅผ ์์ฑํด body์ ๋ถ์ด๋ ๋ฐฉ๋ฒ

<div class="codebox-title">main.js</div>

```javascript
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
            โฎ
renderer.render(scene, camera);
```

<br />

2. body์ ๋ง๋ค์ด๋ canvasํ๊ทธ๋ฅผ ์ฌ์ฉํด renderer์ ์ง์ ํด์ฃผ๋ ๋ฐฉ๋ฒ
<div class="codebox-title">index.html</div>

```html
<body>
  <canvas id="three-canvas"></canvas>
</body>
```

<div class="codebox-title">main.js</div>

```javascript
const canvas = document.querySelector('#three-canvas');
const renderer = new THREE.WebGLRenderer({ canvas });
renderer.setSize(window.innerWidth, window.innerHeight);
            โฎ
renderer.render(scene, camera);
```

<br />

### ๐ Scene

Scene๊ฐ์ฒด๋ ํ๋ฉด์ ๊ตฌ์ฑํ๋ `๋ฌผ์ฒด(Object)`์ `๊ด์(Light)`๋ฅผ ์ ์ ํ๊ณ  ๊ด๋ฆฌํ๋ ์ญํ ์ ํฉ๋๋ค. ๋ฌผ์ฒด์ ๊ด์์ ์์ฑํ ๋ค, ํด๋น ๊ฐ์ฒด๋ฅผ Scene๊ฐ์ฒด์ ํฌํจ์์ผ์ผ ํ๋ฉด์ ๋ํ๋ฉ๋๋ค.
ํด๋น ๊ฐ์ฒด๋ ์ถํ์ ๋ ์์ธํ ์ค๋ชํด๋ณด๊ฒ ์ต๋๋ค.

<div class="codebox-title">main.js</div>

```javascript
const scene = new THREE.Scene();
scene.fog = new THREE.Fog('blue', 1.5, 7);

const light = new THREE.DirectionalLight(0xffffff, 1);
light.position.x = 1;
light.position.y = 3;
light.position.z = 5;
scene.add(light);
```

![์๊ฐ์ ๊ด์ ํจ๊ณผ ์ถ๊ฐ](./basic-of-threejs-07.png)

<p class="img-caption" style="margin: -5px 10px 0 10px;">
    ๊ด์์ด ์์ด์ผ ๋ณด์ด๋ 3D Object์ ์ฌ์ฉํ์ต๋๋ค. ์๊ฐ์์ ๋ฐฐ๊ฒฝ์ ๊ฐ์ ์์ ์ฌ์ฉํ๋ฉด <b>Shadow</b>ํจ๊ณผ๋ฅผ ๋ผ ์ ์์ต๋๋ค.
</p>
<br />

### ๐ท Camera

์นด๋ฉ๋ผ๋ Scene๊ฐ์ฒด๋ฅผ ์ดฌ์ํ์ฌ ์ด๋ป๊ฒ ๋ณด์ฌ์ค ๊ฒ์ธ๊ฐ๋ฅผ ๊ฒฐ์ ํฉ๋๋ค. ๊ฐ์ Scene์ด๋ผ๋ ์นด๋ฉ๋ผ์ ์์น ๋ฐ ๊ธฐํ ์ค์ ๊ฐ๋ค์ ํตํด์ ๋ค๋ฅธ ํ๋ฉด์ ๋ณด์ฌ์ค ์ ์์ต๋๋ค.

![์นด๋ฉ๋ผ ์ ๋์ฒด(viewing frustum)](./basic-of-threejs-04.gif)

<p class="img-caption" style="margin: -15px 10px 0 10px;">
    ์์ผ๊ฐ, ์ขํก๋น, <span style="color: rgb(110, 250,34)">near</span>, <span style="color: rgb(228, 64, 36)">far</span>์ ๋ฐ๋ผ ๋ณด์ด๋ Scene์ด ๋ณํฉ๋๋ค.
</p>
<br />

Camera๋ `PerspectiveCamera`์ `OrthographicCamera`๊ฐ ์๋๋ฐ ๊ฐ์ฒด๋ณ ์ฝ๋์ ๊ฒฐ๊ณผ๋ฅผ ํ์ธํด๋ด์๋ค.

<div class="codebox-title">main.js - Perspective Camera</div>

```javascript
const camera = new THREE.PerspectiveCamera(
  75, // fov(์์ผ๊ฐ)
  window.innerWidth / window.innerHeight, // aspect(์ขํก๋น)
  0.1, // near
  1000, // far
);
// camera ์์น ์ค์ 
camera.position.x = 1;
camera.position.y = 2;
camera.position.z = 5;
scene.add(camera);
```

<div class="codebox-title">main.js - Orthographic Camera</div>

```javascript
const camera = new THREE.OrthographicCamera(
  -(window.innerWidth / window.innerHeight), // left
  window.innerWidth / window.innerHeight, //right
  1, //top
  -1, //bottom
  0.1, // near
  1000, // far
);
// camera ์์น ์ค์ 
camera.position.x = 1;
camera.position.y = 2;
camera.position.z = 10;
camera.lookAt(0, 0, 0);
// updateProjectionMatrix ์นด๋ฉ๋ผ ์์ฑ ์๋ฐ์ดํธ์ ํธ์ถํ๋ ํจ์
camera.zoom = 0.5;
camera.updateProjectionMatrix();

scene.add(camera);
```

<div class="img-wrapper">
    <img src="./basic-of-threejs-05.png" alt="์๊ทผ ์นด๋ฉ๋ผ(Perspective Camera)"/>
    <img src="./basic-of-threejs-06.png" alt="์ง๊ต ์นด๋ฉ๋ผ(Orthographic Camera)"/>
</div>
<p class="img-caption" style="margin: 10px 10px 0 10px;">
    ์ผ์ชฝ์ด <b>Perspective Camera</b>, ์ค๋ฅธ์ชฝ์ด <b>Orthographic Camera</b>๋ก ๋ด๊ธด Scene์๋๋ค.
</p>
<br/>

**Perspective Camera**๋ ๊ฐ๊น์ด ์๋ ๊ฒ์ ํฌ๊ฒ, ๋ฉ๋ฆฌ ์๋๊ฒ์ ์์ ๋ณด์ด๋ ์๊ทผ๋ฒ์ด ์ ์ฉ๋ ๊ฒ์ ํ์ธํ  ์ ์์ต๋๋ค.
๋ฐ๋ฉด์ **Orthographic Camera**๋ ์๊ทผ๋ฒ์ด ์ ์ฉ๋์ง ์๊ณ  ์นด๋ฉ๋ผ์ z์ถ ์์น์๋ ์๊ด์์ด Object๋ค์ ํฌ๊ธฐ๊ฐ ์ผ์ ํ๊ฒ ๋ณด์ด๋๊ฒ์ ํ์ธํ  ์ ์์ต๋๋ค.
<br />

### ๐ฆ Mesh

Mesh๋ 3Dํ๋ฉด์ ๊ตฌ์ฑํ๋ ๋ฌผ์ฒด๋ก, ์ด๋ค `Material`๋ก ํ๋์ `Geometry`๋ฅผ ๊ทธ๋ฆฌ๋ ๊ฐ์ฒด์๋๋ค. Mesh๊ฐ ๋ง๋ค์ด์ง๋ฉด ์ค์ ๊ฐ์ ํตํด 3D ๊ณต๊ฐ์์ ์์น์ ์์ธ๋ฅผ ๊ฒฐ์ ํ  ์ ์์ต๋๋ค.
Material,Geometry๋ **์ฌ์ฌ์ฉ์ด ๊ฐ๋ฅ**ํ์ฌ ์ฌ๋ฌ๊ฐ์ Mesh๊ฐ ํ๋์ Material ๋๋ Geometry๋ฅผ ๋์์ ์ฐธ์กฐํ  ์ ์์ต๋๋ค. ์๋์ ์ฝ๋๋ฅผ ํตํด **๊ด์์ ์ํฅ์ ๋ฐ๋ ํ๋์ ์ ์ก๋ฉด์ฒด**๋ฅผ ๋ง๋ค ์ ์์ต๋๋ค.

<div class="codebox-title">main.js</div>

```javascript
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshStandardMaterial({
  color: 'red',
});
const mesh = new THREE.Mesh(geometry, material);
mesh.rotation.y = 2;
scene.add(mesh);
```

---

๋ค์ ํฌ์คํ์์๋ **3D ์ค๋ธ์ ํธ์ ์ด๋ป๊ฒ ์ ๋๋ฉ์ด์ ํจ๊ณผ๋ฅผ ๋ถ์ฌํ๋์ง**์ ๋ํด ์์๋ณด๊ฒ ์ต๋๋ค.
๐ฅณ

```toc

```
