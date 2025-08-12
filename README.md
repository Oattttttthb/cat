# cat<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>แมวส้มขนสั่น</title>
<style>
  body {
    background-color: #fff5e6;
    text-align: center;
    font-family: 'Comic Sans MS', cursive, sans-serif;
    overflow-x: hidden;
  }
  h1 {
    color: #ff6600;
  }
  .cat {
    width: 200px;
    cursor: pointer;
    transition: transform 0.2s ease;
    position: relative;
  }
  .bounce {
    animation: bounce 0.4s ease;
  }
  @keyframes bounce {
    0%   { transform: scale(1); }
    30%  { transform: scale(1.1); }
    50%  { transform: scale(0.95); }
    70%  { transform: scale(1.05); }
    100% { transform: scale(1); }
  }
  .message {
    font-size: 1.5em;
    color: #ff6600;
    margin-top: 20px;
    height: 2em;
  }
  .counter {
    font-size: 1.2em;
    margin-top: 10px;
    color: #ff9966;
  }
  .heart {
    position: absolute;
    font-size: 2em;
    animation: floatUp 1s ease forwards;
    pointer-events: none;
  }
  @keyframes floatUp {
    0% { transform: translateY(0); opacity: 1; }
    100% { transform: translateY(-100px); opacity: 0; }
  }
</style>
</head>
<body>

<h1>🐾 แมวส้มขนสั่น 🐾</h1>
<div style="position: relative; display: inline-block;">
<img src="https://i.imgur.com/ydNO6lC.png" alt="แมวส้ม" class="cat" id="cat">
</div>
<div class="message" id="message"></div>
<div class="counter" id="counter">กดแล้ว: 0 ครั้ง</div>

<audio id="meow-sound" src="https://www.fesliyanstudios.com/play-mp3/387" preload="auto"></audio>

<script>
  const messages = [
    "รักนะครับ ❤️",
    "คิดถึงจังครับ 🐾",
    "น่ารักจังเลย 😻",
    "จุ๊บๆ นะครับ 💋"
  ];

  let clickCount = 0;
  const cat = document.getElementById("cat");
  const message = document.getElementById("message");
  const counter = document.getElementById("counter");
  const meowSound = document.getElementById("meow-sound");

  cat.addEventListener("click", (event) => {
    clickCount++;
    const randomMessage = messages[Math.floor(Math.random() * messages.length)];
    message.textContent = randomMessage;
    counter.textContent = `กดแล้ว: ${clickCount} ครั้ง`;

    // เล่นเสียงแมว
    meowSound.currentTime = 0;
    meowSound.play();

    // อนิเมชันเด้ง
    cat.classList.remove("bounce");
    void cat.offsetWidth;
    cat.classList.add("bounce");

    // หัวใจลอย
    const heart = document.createElement("div");
    heart.textContent = "❤️";
    heart.className = "heart";
    heart.style.left = (event.offsetX - 10) + "px";
    heart.style.top = (event.offsetY - 20) + "px";
    cat.parentElement.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 1000);
  });
</script>

</body>
</html>
