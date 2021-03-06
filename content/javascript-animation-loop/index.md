---
emoji: ๐จ
title: ์ด๋ค Animation Loop๋ฅผ ์ฌ์ฉํ๋๊ฒ ์ข์๊น?
date: '2022-04-05 14:30:00'
author: ํ์ง์
tags: ๋ธ๋ก๊ทธ javascript canvas animation
categories: Javasctipt featured
---

## ๐ค Animation Loop๋ ์ธ์  ์คํ๋๋์?

![DOM Performance](./javascript-animation-loop-01.png)

<p class="img-caption" style="margin: -20px 10px 0 10px;">
๋ธ๋ผ์ฐ์ ์ ๋ ๋๋ง ๊ณผ์ ์ ์ผ๋ถ๋ถ
</p>
<br />

Animation Loop๋ ๋ธ๋ผ์ฐ์  ๋ ๋๋ง ๊ณผ์ ์์ `repaint` ์ด์  ๋จ๊ณ์์ ์งํ๋ฉ๋๋ค.

> **Reflow** <br /> ๋ชจ๋  ์์์ ํฌ๊ธฐ์ ์์น๋ฅผ ๋ค์ ๊ณ์ฐํ๋ ๊ณผ์  <br /> **Repaint** <br /> reflow ๋ค์ ๋จ๊ณ, ๋ ์ด์์์ ์ ์ธํ ์์๊ฐ ๊ทธ๋ ค์ง๋ ๊ณผ์ <br /> **Composite** <br />๋ค์ํ ์์๋ฅผ ๋ ์ด์ด๋ก ๊ทธ๋ฃนํํ๊ณ  ์ด๋ฌํ ๋ ์ด์ด๋ฅผ ๋์คํฐํ๋ ๊ณผ์ 

---

## ๐ฎ SetInterval

### โก๏ธ setInterval์ด๋ ๋ฌด์์ผ๊น?

requestAnimationFrame์ ๋ฑ์ฅ ์ด์ ์ ์๋ฐ์คํฌ๋ฆฝํธ ์ ๋๋ฉ์ด์ ๊ตฌํ์ `setTimeout`๊ณผ ์ฃผ๋ก ์ฌ์ฉ๋๋ ํจ์๋ผ๊ณ  ํฉ๋๋ค.
setInterval์ ๋๋ฒ์งธ ์ธ์์ `์ธํฐ๋ฒ`์ ๊ธฐ์ํด ์ ๋๋ฉ์ด์์ **๋ฐ๋ณต ์๋๋ฅผ ์กฐ์ **ํ  ์ ์๋ ์ฅ์ ์ด ์์ต๋๋ค.
ํ์ง๋ง ๋์คํ๋ ์ด ์ฑ๋ฅ์ ๊ณ ๋ คํ์ง ์์ ์งง์ ์๋ฐ์ดํธ ์ฃผ๊ธฐ ๋๋ฌธ์ ์ ๋๋ฉ์ด์์ **ํ๋ ์ ๋๋**์ด ๋ฐ์ํ๋ ๋จ์ ์ด ์์ต๋๋ค.

![setInterval, setTimeout flow](./javascript-animation-loop-02.png)

<p class="img-caption" style="margin: -15px 10px 0 10px;">
Jank: ์คํฌ๋กค, ์ ํ ๋๋ ์ ๋๋ฉ์ด์๊ณผ ๊ฐ์ด ํ๋ฉด์ ์์ง์์ด ์์ ๋ ์ฌ์ฉ์๊ฐ ๊ฒฝํํ๋ ๋ฒ๋ฒ๊ฑฐ๋ฆผ
</p>
<br />

### โก๏ธ setInterval๋ก ์์ฑํ ์ ๋๋ฉ์ด์

์๊ฐ์ ํ๋ฆ์ ๋ฐ๋ผ ์๋ชฝ๊ฐ๊ฐ ์ผ์ชฝ์ผ๋ก ์ด๋ํ๋ ์ ๋๋ฉ์ด์์ ์์ฑํ์ต๋๋ค.
fps๊ฐ๋ ๊ณ์ฐํ์ผ๋ ํ๋จ์์ requestAnimationFrame๊ณผ ๊ฒฐ๊ณผ๋ฅผ ๋น๊ตํด๋ด์๋ค.

<div class="codebox-title">index.html - setInterval</div>

```javascript
const ele = document.querySelector('#emolga');
const pVal = document.querySelector('#p_value');
const cVal = document.querySelector('#c_value');

let xPos = 0;
let start = performance.now();
let timer;

const render = () => {
  if (xPos >= 500) clearInterval(timer);
  // ์๋ชฝ๊ฐ x์ถ ์ด๋
  pVal.innerHTML = xPos;
  xPos += 1;
  ele.style.transform = `translateX(-${xPos}px)`;
  // ์ฝ๋ฐฑ ํธ์ถ ์ฃผ๊ธฐ ๊ณ์ฐ
  let action = performance.now();
  let diff = Math.trunc(action - start);
  start = action;
  cVal.innerHTML = `${diff}ms (${Math.trunc(1000 / diff)}fps)`;
};
timer = setInterval(render);
```

<br />

## ๐ฎ requestAnimationFrame

### โก๏ธ requestAnimationFrame์ด๋ ๋ฌด์์ผ๊น?

๋ธ๋ผ์ฐ์ ์๊ฒ ์ํํ๊ธฐ๋ฅผ ์ํ๋ ์ ๋๋ฉ์ด์์ ์๋ฆฌ๊ณ  ๋ค์ `repaint`๊ฐ ์งํ๋๊ธฐ ์ ์ ํด๋น ์ ๋๋ฉ์ด์์ ์๋ฐ์ดํธํ๋ ํจ์๋ฅผ ๋์คํ๋ ์ด์ `ํ๋ฉด ์ฃผ์ฌ์จ`์ ๋ฐ๋ฅธ ์ฃผ๊ธฐ๋ก ํธ์ถํ๊ฒ ํฉ๋๋ค.
**60ํ๋ ์**์ ๋ชฉํ๋ก ๋์ํ๊ธฐ ๋๋ฌธ์ ์ฌ์ฉ์์๊ฒ ๋ณด๋ค ๋์ ๊ฒฝํ์ ์ ์ฌํ  ์ ์์ต๋๋ค.๐

![requestAnimaionFrame flow](./javascript-animation-loop-03.png)

### โก๏ธ requestAnimationFrame๋ก ์์ฑํ ์ ๋๋ฉ์ด์

์๋จ์ setInterval๊ณผ ๋์ผํ ๋์์ ์ํํ๋ ์ ๋๋ฉ์ด์์ ์์ฑํ์ต๋๋ค.
์๋์์ ๋์ ๊ฒฐ๊ณผ๋ฅผ ๋น๊ตํด๋ด์๋ค.

<div class="codebox-title">index.html - requestAnimationFrame</div>

```javascript
const ele = document.querySelector('#emolga');
const pVal = document.querySelector('#p_value');
const cVal = document.querySelector('#c_value');

let xPos = 0;
let start = performance.now();
let animationId;

const requestRender = () => {
  // ์๋ชฝ๊ฐ x์ถ ์ด๋
  pVal.innerHTML = xPos;
  xPos += 1;
  ele.style.transform = `translateX(-${xPos}px)`;
  // ์ฝ๋ฐฑ ํธ์ถ ์ฃผ๊ธฐ ๊ณ์ฐ
  let action = performance.now();
  let diff = Math.trunc(action - start);
  start = action;
  cVal.innerHTML = `${diff}ms (${Math.trunc(1000 / diff)}fps)`;

  animationId = requestAnimationFrame(requestRender);
  if (xPos > 500) cancelAnimationFrame(animationId);
};
requestAnimationFrame(requestRender);
```

<br />

## ๐ฉโ๐ป ์ด์  ๊ฒฐ๊ณผ๋ฅผ ๋น๊ตํด ๋ด์๋ค

<video src="javascript-animation-loop-04.mov" loop muted Autoplay=autoplay style="width: 100%; height: 100%; object-fit: cover;"></video>

<p class="img-caption" style="margin: -25px 10px 0 10px;">
setInterval๊ณผ requestAnimationFrame์ ์คํํ ํ๋ฉด, ํด๋น ์์์ 120Hz์ ๋์คํ๋ ์ด์์ ๋นํํ์ต๋๋ค.
</p>
<br />

๋ ํจ์ ๋์ผํ๊ฒ 500๋ฒ ๋ฐ๋ณต๋  ๋์ ๊ฐ๊ฐ **250fps** ์ **120fps**์ ์๋๋ก ์ ๋๋ฉ์ด์์ด ๊ตฌ๋ํ์์ ํ์ธํ  ์ ์์ต๋๋ค. setInterval๊ณผ ๋ค๋ฅด๊ฒ `requestAnimationFrame`์ ๋์คํ๋ ์ด์ ํ๋ฉด ์ฃผ์ฌ์จ์ ๋ง์ถฐ ์ ๋๋ฉ์ด์์ ์๋ฐ์ดํธํ์์ ํ์ธํ  ์ ์์ต๋๋ค.
<br />
์ฌ๊ธฐ์๋ ์ธ๊ธ์ด ์์์ง๋ง, ๋ค๋ฅธ ํญ์ผ๋ก ์ด๋ํ๋ฉด setInterval์ ๊ณ์ํด์ ๋์ํ์ง๋ง requestAnimationFrame๋ **๋์์ ์ผ์์ค์ง**ํฉ๋๋ค. **๋ณต์กํ๊ณ  ํฐ ์ ๋๋ฉ์ด์**์ ์์์ ํ  ๊ฒฝ์ฐ์๋ `requestAnimationFrame`์ ํจ๊ณผ๋ ๋ ๋๋๋ฌ์ง ๊ฒ์๋๋ค.

---

## ๐ ๊ทธ๋์ ์ด๋ค ํจ์๊ฐ ์ ๋๋ฉ์ด์์ ๋ ์ ํฉํ๊ฐ์?

**requestAnimationFrame**์ ๋ค์๊ณผ ๊ฐ์ ์ด์ ๋ก ์ถ์ฒํฉ๋๋ค!๐ ๐

1. ๋ธ๋ผ์ฐ์ ๊ฐ **`repaint`๋ฅผ ์คํํ๋ ค ํ  ๋ ๋๊ธฐํ**ํฉ๋๋ค.
2. **์ ๋๋ฉ์ด์์ ์ต์ ํ**๋ ํจ์์ด๋ฉฐ, **`60fps`๋ฅผ ๋ชฉํ๋ก ๋์**ํ๋ฉฐ ๋์คํ๋ ์ด์ ๋ฐ๋ผ ๋ ๋์ ํ๋ ์๋ฅ ์ ๋ณด์๋๋ค.
3. ๋ธ๋ผ์ฐ์ ๊ฐ ํ๋ ์ผ์ ๋ฐ๋ผ **ํจ์์ ์๋๋ฅผ ์กฐ์ ํ๊ณ  ์ผ์์ค์ง** ํฉ๋๋ค.
4. ๋ธ๋ผ์ฐ์  ์ํ์ ๋ฐ๋ผ ํจ์๊ฐ ์ผ์์ค์ง๋๊ธฐ์, **`CPU ๋ฆฌ์์ค`์ `๋ฐฐํฐ๋ฆฌ ์๋ช`์ ๋ญ๋นํ์ง ์์ต๋๋ค.**
5. **๋ชจ๋  `์ต์  ๋ฐ์คํฌํฑ` ๋ฐ `๋ชจ๋ฐ์ผ ๋ธ๋ผ์ฐ์ `์์ ์ง์๋ฉ๋๋ค.**

**๐ค ์ต๊ทผ๋ค์ด ์ ๋๋ฉ์ด์์ ๊ตฌํํ๊ธฐ ์ํด์ setInterval๊ณผ setTimeout์ ์ฌ์ฉํ์ง ์๋ ์ถ์ธ์๋๋ค.๐ค**

<br />

## ๐ ๋ธ๋ผ์ฐ์  ๋ฒค๋๋ฅผ ๊ณ ๋ คํ๋ค๋ฉด!

<div class="codebox-title">script.js</div>

```javascript
const requestAnimationFrame =
  window.requestAnimationFrame ||
  window.mozRequestAnimationFrame ||
  window.webkitRequestAnimationFrame ||
  window.msRequestAnimationFrame;
```

**requesetAnimationFrame์ ์ง์ํ์ง ์๋ ํ๊ฒฝ๊น์ง ๊ณ ๋ คํ๋ค๋ฉด**

<div class="codebox-title">script.js</div>

```javascript
const requestAnimationFrame = (() => {
  return (
    window.requestAnimationFrame ||
    window.webkitRequestAnimationFrame ||
    window.mozRequestAnimationFrame ||
    window.oRequestAnimationFrame ||
    window.msRequestAnimationFrame ||
    ((callback) => {
      window.setTimeout(callback, 1000 / 60);
    })
  );
})();
```

---

ํ๋ฆฐ ์ค๋ช ํน์ ๋ณด์ถฉ์ด ํ์ํ ์ค๋ช์ ์ฝ๋ฉํธ ๋ฌ์์ฃผ์๋ฉด ๊ฐ์ฌํ๊ฒ ์ต๋๋ค! ๐

```toc

```
