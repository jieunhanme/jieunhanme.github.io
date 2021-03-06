---
emoji: ๐ฏ
title: Threejs์ ์ฑ๋ฅ ํฅ์์ ๋์์ ์ฃผ๋ ์์ํ ํ
date: '2022-04-05 20:30:00'
author: ํ์ง์
tags: ๋ธ๋ก๊ทธ threejs 3d WebGL
categories: Threejs
---

## ๐ ๊ณ๋จ ํ์์ ๊ฑฐ

<div class="codebox-title">main.js</div>

```javascript
const renderer = new THREE.WebGLRenderer({
  canvas,
  antialias: true, // ๊ณ๋จํ์ ์ ๊ฑฐ >> (๋ฏธ๋ฏธํ) ์ฑ๋ฅ ์ ํ ๊ฐ๋ฅ์ฑ ์์
});
```

<br />

## ๐ ํฝ์ ๋ฐ๋์ ๋ฐ๋ฅธ ๊ทธ๋ํฝ ์ต์ ํ

> **window.devicePixelRatio** <br /> ํด๋น ๊ธฐ๊ธฐ์ ํฝ์ ๋ฐ๋๋ฅผ ์์นํํด ๋ฐํํฉ๋๋ค. ์์น๊ฐ ๋์์๋ก ๊ณ ํด์๋ ํ๋ฉด์ด ์ ๊ณต๋์ด์ผ ํฉ๋๋ค.

๊ณ ํด์๋๋ก ํํํ๋ค๋ ๊ฒ์ canvas์ ํฌ๊ธฐ๋ฅผ ํ๋ฉด์ 2๋ฐฐ๋ก ๋๋ฆฌ๊ณ  ํด๋น ์ฅ๋ฉด์ ํ๋ฉด ํฌ๊ธฐ๋ก ์์ถํด์ body์ ํํํ๋ ๊ฒ์ ์๋ฏธํฉ๋๋ค.
<br />

<div class="codebox-title">index.html - ์ต์ ํ๊ฐ ์งํ๋ canvas ํ๊ทธ</div>

```html
<canvas
  id="three-canvas"
  data-engine="three.js r138"
  width="3024"
  height="934"
  style="width: 1512px; height: 467px;"
></canvas>
```

window.devicePixelRatio์ ๊ฐ์ด ์์์ด๊ฑฐ๋ ๊ณผํ๊ฒ ํด๊ฒฝ์ฐ ์ฑ๋ฅ ์ ํ๊ฐ ๋ฐ์ํ  ์ ์์ต๋๋ค.
์ค์ ๋ก๋ 1:1 ํน์ 2:1๋์๋ง ํด์ค๋ค๋ฉด ํ์ง์ ๋ฌธ์ ๊ฐ ์๊ธฐ๋๋ฌธ์ 1ํน์ 2์ ๋น์จ๋ก ๊ทธ๋ํฝ ์ต์ ํ๋ฅผ ์งํํฉ๋๋ค.

<div class="codebox-title">main.js</div>

```javascript
renderer.setPixelRatio(window.devicePixelRatio > 1 ? 2 : 1);
```

<br />

## ๐ ํ๋ฉด ์ฌ์ด์ฆ ์๋ ์กฐ์ 

<div class="codebox-title">main.js</div>

```javascript
function setSize() {
  // 1. ์นด๋ฉ๋ผ ์กฐ์ (ํ๋ฉด ์ฌ์ด์ฆ ๋ณ๊ฒฝ === ์นด๋ฉ๋ผ ์ขํก๋น ๋ณ๊ฒฝ)
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();

  // 2. renderer๋ก ๋ค์ ๊ทธ๋ ค์ฃผ๊ธฐ
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.render(scene, camera);
}

// ๋ฆฌ์ฌ์ด์ฆ ์ด๋ฒคํธ ์ถ๊ฐ
window.addEventListener('resize', setSize);
```

<br />

## ๐ ๋ฐฐ๊ฒฝ์ ์์ ์ค์  ๋ฐ ํฌ๋ช๋ ์กฐ์ 

๋ฐฐ๊ฒฝ์ ํฌ๋ช๋๋ `renderer`์ `scene`์์ ์กฐ์ ํด ์ค ์ ์์ต๋๋ค. **๋๊ฐ์ฒด๋ฅผ ํตํด ๊ฐ์ด ์กฐ์ ํด์ค ๊ฒฝ์ฐ ๋ฐฐ๊ฒฝ์์ scene์์ ์ค์ ํ ๊ฐ**์ผ๋ก ๋ฎ์ด์ง๋๋ค.
์๋์ ๊ฐ์ด ์งํ ํ  ๊ฒฝ์ฐ, ๋ถํ์ ๋ฐฐ๊ฒฝ์ผ๋ก ์ค์ ๋ฉ๋๋ค.

<div class="codebox-title">main.js</div>

```javascript
const renderer = new THREE.WebGLRenderer({
  canvas,
  antialias: true,
  alpha: true, // renderer.setClearAlpha(0)์ ๊ฐ์ ๊ฒฐ๊ณผ
});
renderer.setClearColor(0x00ff00, 0.1);

scene.background = new THREE.Color('pink');
```

![๋ฐฐ๊ฒฝ์ ๋ณ๊ฒฝ](./tips-for-threejs-01.png)

```toc

```
