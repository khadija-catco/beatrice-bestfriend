<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Be My Bestfriend Again 💖</title>

  <style>
    body{
      margin:0;
      height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      background:#ffd6e8;
      font-family: Arial, sans-serif;
      overflow:hidden;
    }

    .card{
      background:#fff;
      width:min(440px, 92vw);
      padding:38px 26px;
      border-radius:22px;
      box-shadow: 0 12px 30px rgba(0,0,0,0.18);
      text-align:center;
      position:relative;
      z-index:2;
    }

    h2{ margin:0 0 10px 0; font-size:22px; }
    p{ margin:0 0 18px 0; font-size:16px; line-height:1.4; }

    .buttons{
      position:relative;
      height:130px;
      margin-top:10px;
    }

    button{
      padding:12px 22px;
      border:none;
      border-radius:999px;
      font-size:16px;
      cursor:pointer;
      user-select:none;
    }

    #yesBtn{
      background: hotpink;
      color:#fff;
      box-shadow: 0 8px 18px rgba(255, 0, 128, 0.25);
    }
    #yesBtn:active{ transform: scale(0.98); }

    #noBtn{
      background:#e9e9e9;
      color:#444;
      position:absolute;
      left:58%;
      top:60px;
    }

    .tiny{
      margin-top:14px;
      font-size:12px;
      color:#777;
    }

    .shake{
      animation: shake 0.28s linear;
    }
    @keyframes shake{
      0%{ transform: translateX(0); }
      25%{ transform: translateX(-6px); }
      50%{ transform: translateX(6px); }
      75%{ transform: translateX(-6px); }
      100%{ transform: translateX(0); }
    }

    .heart{
      position:fixed;
      bottom:-30px;
      font-size:18px;
      animation: floatUp linear forwards;
      z-index:1;
      opacity:0.85;
      pointer-events:none;
    }
    @keyframes floatUp{
      to{
        transform: translateY(-110vh);
        opacity:0;
      }
    }

    #beg{
      min-height:18px;
      margin-top:10px;
      font-size:13px;
      color:#ff2f92;
      font-weight:600;
    }
  </style>
</head>

<body>
  <div class="card" id="card">
    <h2>Dear Beatrice S Bangura 💗</h2>
    <p>Will you be my Bestfriend<br><b>again?</b></p>

    <div class="buttons" id="btnArea">
      <button id="yesBtn">Yes 💖</button>
      <button id="noBtn">No 😒</button>
    </div>

    <div id="beg"></div>
    <div class="tiny">Choose wisely 😭</div>
  </div>

  <script>
    const card = document.getElementById("card");
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const btnArea = document.getElementById("btnArea");
    const beg = document.getElementById("beg");

    // 🎵 Apple Music (Raindance – Dave ft Tems)
    const songLink = "https://music.apple.com/search?term=Dave%20Raindance%20Tems";

    // floating hearts
    let heartInterval = setInterval(makeHeart, 450);
    function makeHeart(){
      const h = document.createElement("div");
      h.className = "heart";
      h.textContent = Math.random() > 0.5 ? "💗" : "💕";
      h.style.left = Math.random() * 100 + "vw";
      const duration = 4 + Math.random() * 3;
      h.style.animationDuration = duration + "s";
      h.style.fontSize = (14 + Math.random()*18) + "px";
      document.body.appendChild(h);
      setTimeout(() => h.remove(), duration * 1000);
    }

    // YES = open Apple Music immediately
    yesBtn.addEventListener("click", () => {
      window.open(songLink, "_blank");

      card.innerHTML = `
        <h2>She said YES 🥹💕</h2>
        <p>Bestfriends again.<br>Forever this time 🤞🏽💗</p>
        <p class="tiny">This song is for you 🎶💖</p>
      `;
    });

    // NO runs away
    noBtn.addEventListener("mouseenter", tryNo);
    noBtn.addEventListener("touchstart", (e) => {
      e.preventDefault();
      tryNo();
    }, { passive:false });

    function tryNo(){
      beg.textContent = "Beatrice please 😭 just press YES 💗";
      noBtn.classList.remove("shake");
      void noBtn.offsetWidth;
      noBtn.classList.add("shake");
      moveNo();
    }

    function moveNo(){
      const areaRect = btnArea.getBoundingClientRect();
      const btnRect = noBtn.getBoundingClientRect();
      const maxX = areaRect.width - btnRect.width;
      const maxY = areaRect.height - btnRect.height;
      noBtn.style.left = `${Math.random() * Math.max(0, maxX)}px`;
      noBtn.style.top = `${Math.random() * Math.max(0, maxY)}px`;
    }
  </script>
</body>
</html>
