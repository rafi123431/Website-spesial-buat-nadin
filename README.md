<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Untuk Nadin dari Rafi</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');
  /* Reset */
  * {
    margin: 0; padding: 0; box-sizing: border-box;
  }
  body, html {
    height: 100%;
    font-family: 'Poppins', sans-serif;
    background: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1471&q=80') no-repeat center center fixed;
    background-size: cover;
    overflow: hidden;
    transition: background 1s ease;
  }
  /* Body black background after login */
  body.black-bg {
    background: #000000;
  }
  /* Overlay purple with blur */
  body::before {
    content: "";
    position: fixed;
    top:0; left:0; width:100%; height:100%;
    background: rgba(102,51,153, 0.5); /* Keunguan purple overlay */
    backdrop-filter: blur(8px);
    z-index: -1;
    transition: background 1s ease, backdrop-filter 1s ease;
  }
  /* Remove overlay when black-bg */
  body.black-bg::before {
    background: transparent;
    backdrop-filter: none;
  }
  #container {
    position: relative;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: #eee;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 0 15px;
  }
  .slide {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    max-width: 400px;
    transform: translate(-50%, -50%);
    opacity: 0;
    transition: opacity 1.2s ease;
    user-select: none;
  }
  .slide.active {
    opacity: 1;
    position: relative;
  }
  /* Blur class for slides to blur */
  .slide.blur {
    filter: blur(6px);
    transition: filter 1.3s ease;
  }
  /* First slide text */
  #slide1 h1 {
    font-weight: 600;
    font-size: 2.2rem;
    margin-bottom: 0.3em;
    color: #dcc9f0;
    text-shadow: 0 2px 8px rgba(0,0,0,0.4);
  }
  #slide1 p {
    font-weight: 400;
    font-size: 1.2rem;
    color: #e9defa;
    line-height: 1.5;
    max-width: 320px;
    margin: 0 auto;
    text-shadow: 0 1px 6px rgba(0,0,0,0.3);
  }

  /* Tulip slide */
  #slide2 {
    display: flex;
    justify-content: center;
    align-items: flex-end;
    height: 320px;
  }

  .tulip {
    position: relative;
    width: 80px;
    height: 250px;
  }

  /* Stem */
  .stem {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 14px;
    height: 180px;
    background: linear-gradient(to top, #2e7d32, #4caf50);
    border-radius: 20px 20px 3px 3px;
    transform-origin: bottom center;
    filter: drop-shadow(0 1px 1px rgba(0,0,0,0.2));
    animation: growStem 3s ease forwards;
  }
  @keyframes growStem {
    from {height: 0;}
    to {height: 180px;}
  }

  /* Leaves */
  .leaf {
    position: absolute;
    width: 36px;
    height: 80px;
    background: linear-gradient(135deg, #388e3c, #66bb6a);
    border-radius: 50% 50% 50% 50% / 70% 70% 30% 30%;
    top: 80px;
    left: 10px;
    transform-origin: left center;
    filter: drop-shadow(0 1px 1px rgba(0,0,0,0.2));
    animation: growLeafLeft 3s ease forwards;
  }
  .leaf.right {
    left: auto;
    right: 10px;
    top: 80px;
    transform-origin: right center;
    animation: growLeafRight 3s ease forwards;
  }
  @keyframes growLeafLeft {
    from {height: 0; opacity: 0;}
    to {height: 80px; opacity: 1;}
  }
  @keyframes growLeafRight {
    from {height: 0; opacity: 0;}
    to {height: 80px; opacity: 1;}
  }

  /* Flower petals container */
  .flower {
    position: absolute;
    bottom: 180px;
    left: 50%;
    transform: translateX(-50%) scale(0);
    width: 140px;
    height: 140px;
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.25));
    animation: growFlower 3s ease forwards 3s;
  }
  @keyframes growFlower {
    to {transform: translateX(-50%) scale(1);}
  }

  /* Petal style and sparkles */
  .petal {
    position: absolute;
    width: 60px;
    height: 80px;
    background: radial-gradient(ellipse at center, #f8bbd0 40%, #ec407a 95%);
    border-radius: 50% 50% 55% 55% / 70% 70% 30% 30%;
    filter: drop-shadow(0 1px 3px rgba(236,64,122,0.5));
    opacity: 0.9;
    animation: sparkle 2.5s ease-in-out infinite alternate;
    box-shadow:
      0 0 8px 4px rgba(255,192,203,0.7),
      0 0 15px 7px rgba(255,105,180,0.5);
  }
  @keyframes sparkle {
    0% {filter: drop-shadow(0 1px 3px rgba(236,64,122,0.5)) brightness(0.9);}
    100% {filter: drop-shadow(0 1px 10px rgba(236,64,122,1)) brightness(1.3);}
  }

  /* Petal positions */
  .petal1 { top: 0; left: 40%; transform: rotate(-25deg);}
  .petal2 { top: 0; left: 0; transform: rotate(25deg);}
  .petal3 { top: 25px; left: 20%; transform: rotate(0deg);}
  .petal4 { top: 20px; left: 45%; transform: rotate(35deg);}
  .petal5 { top: 20px; left: 85%; transform: rotate(-10deg);}

  /* Hearts falling */
  #slide3 {
    width: 100%;
    height: 100%;
    pointer-events: none;
  }
  .heart {
    position: fixed;
    color: #e91e63;
    font-size: 1.4rem;
    user-select: none;
    animation-name: fall;
    animation-timing-function: linear;
    animation-iteration-count: 1;
  }
  @keyframes fall {
    0% {transform: translateY(-30px) scale(1) rotate(0deg); opacity:1;}
    80% {opacity: 1;}
    100% {transform: translateY(100vh) scale(0.8) rotate(360deg); opacity: 0;}
  }

  /* Final quote slide styles */
  #slide4 {
    max-width: 500px;
    color: #f3e5f5;
    font-style: italic;
    backdrop-filter: none;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
  }
  #slide4 h2 {
    font-size: 1.6rem;
    line-height: 1.4;
    text-shadow: 2px 3px 7px rgba(0, 0, 0, 0.7);
    margin-bottom: 0.8em;
  }
  #slide4 .author {
    font-size: 1rem;
    font-weight: 600;
    margin-top: -8px;
  }
</style>
</head>
<body>
<div id="container">
  <!-- Slide 1: Login page text -->
  <div id="slide1" class="slide active" aria-label="Login message for Nadin">
    <h1>halo nadin sayang</h1>
    <p>Aku belajarbikin website ini sendirian, khusus buat nadin</p>
  </div>
  <!-- Slide 2: Tulip animation -->
  <div id="slide2" class="slide" aria-label="Tulip flower animation">
    <div class="tulip" aria-hidden="true">
      <div class="stem"></div>
      <div class="leaf"></div>
      <div class="leaf right"></div>
      <div class="flower">
        <div class="petal petal1"></div>
        <div class="petal petal2"></div>
        <div class="petal petal3"></div>
        <div class="petal petal4"></div>
        <div class="petal petal5"></div>
      </div>
    </div>
  </div>
  <!-- Slide 3: Falling hearts -->
  <div id="slide3" class="slide" aria-label="Love hearts falling animation">
    <!-- hearts will be dynamically created -->
  </div>
  <!-- Slide 4: Final quote -->
  <div id="slide4" class="slide" aria-label="Love quote for Nadin">
    <h2>aku sayang banget sama nadin,<br/> nadin jangan berpaling dari aku ya</h2>
    <div class="author">by Rafi</div>
  </div>
</div>
<script>
  const slides = [...document.querySelectorAll('.slide')];

  function showSlide(index) {
    slides.forEach((s,i) => {
      s.classList.toggle('active', i === index);
    });
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.textContent = '❤';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = 3000 + Math.random() * 4000 + 'ms';
    heart.style.fontSize = (14 + Math.random() * 10) + 'px';
    heart.style.opacity = 0.8 + Math.random() * 0.2;
    document.getElementById('slide3').appendChild(heart);
    heart.addEventListener('animationend', () => heart.remove());
  }

  let heartInterval;

  function startHearts() {
    heartInterval = setInterval(createHeart, 350);
  }
  function stopHearts() {
    clearInterval(heartInterval);
  }

  async function wait(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  }

  async function startSequence() {
    showSlide(0);
    await wait(4000);

    showSlide(1);
    document.body.classList.add('black-bg');
    await wait(7000);

    showSlide(2);
    startHearts();
    await wait(7000);
    stopHearts();

    slides.forEach((slide, idx) => {
      if (idx !== 3) {
        slide.classList.add('blur');
      } else {
        slide.classList.remove('blur');
      }
    });
    showSlide(3);
  }

  window.onload = () => {
    startSequence();
  };
</script>
</body>
</html>
