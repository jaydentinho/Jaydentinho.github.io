# Jaydentinho.github.io
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />  
  <title>💌 For Kayt-Linn</title>  
  <style>  
    :root{  
      --pink:#ff4d6d;  
      --soft:#fff1f4;  
      --text:#222;  
    }  
    *{box-sizing:border-box}  
    body{  
      margin:0;  
      height:100vh;  
      display:flex;  
      align-items:center;  
      justify-content:center;  
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);  
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "Segoe UI", Roboto, Arial, sans-serif;  
      color:var(--text);  
      padding:16px;  
      overflow:hidden;  
      -webkit-tap-highlight-color: transparent;  
    }  
    .card{  
      width:min(420px, 94vw);  
      background:white;  
      border-radius:24px;  
      padding:22px 18px 18px;  
      box-shadow: 0 18px 40px rgba(0,0,0,.18);  
      position:relative;  
      text-align:center;  
    }  
    .pill{  
      display:inline-block;  
      background:var(--soft);  
      border:1px solid rgba(255,77,109,.25);  
      color:var(--pink);  
      padding:8px 12px;  
      border-radius:999px;  
      font-weight:700;  
      font-size:13px;  
      margin-bottom:10px;  
    }  
    h1{  
      margin:8px 0 8px;  
      font-size:24px;  
      line-height:1.15;  
      color:var(--pink);  
    }  
    p{  
      margin:8px 0;  
      font-size:16px;  
      line-height:1.35;  
    }  
    .question{  
      margin-top:12px;  
      font-size:18px;  
      font-weight:800;  
    }  
    .buttons{  
      margin-top:16px;  
      display:flex;  
      gap:12px;  
      justify-content:center;  
      flex-wrap:wrap;  
    }  
    button{  
      border:none;  
      border-radius:16px;  
      padding:14px 18px;  
      font-size:18px;  
      font-weight:800;  
      cursor:pointer;  
      min-width:140px;  
      transition: transform .18s ease, filter .18s ease;  
      touch-action: manipulation;  
    }  
    button:active{ transform: scale(0.98); }  
  
    #yes{  
      background:var(--pink);  
      color:white;  
      box-shadow: 0 10px 20px rgba(255,77,109,.28);  
    }  
    #yes:hover{ filter: brightness(1.02); }  
  
    #no{  
      background:#e9e9ee;  
      color:#444;  
      position:relative;  
    }  
  
    .tease{  
      margin-top:14px;  
      min-height:22px;  
      font-weight:800;  
      color:var(--pink);  
    }  
  
    .hidden{ display:none; }  
  
    .result h1{ font-size:26px; }  
    .result p{ font-size:16px; }  
  
    /* Confetti hearts */  
    .conf{  
      position:fixed;  
      top:-24px;  
      font-size:20px;  
      pointer-events:none;  
      animation: fall 3s linear forwards;  
      will-change: transform, opacity;  
    }  
    @keyframes fall{  
      to{  
        transform: translateY(110vh) rotate(360deg);  
        opacity:0;  
      }  
    }  
  
    /* iPhone safe area padding */  
    @supports (padding: max(0px)) {  
      .card { padding-bottom: max(18px, env(safe-area-inset-bottom)); }  
    }  
  </style>  
</head>  
<body>  
  
  <div class="card" id="card">  
    <div class="pill">From Jayden 💘 (typed with love)</div>  
  
    <h1>Hi Kayt-Linn 🥹</h1>  
    <p>I have a very important, extremely serious, absolutely life-changing question…</p>  
    <p class="question">Will you be my Valentine?</p>  
  
    <div class="buttons" id="buttons">  
      <button id="yes">YES 💖</button>  
      <button id="no">No 😐</button>  
    </div>  
  
    <div class="tease" id="tease"></div>  
  
    <div class="result hidden" id="result">  
      <h1>YAYYYYY 🎉💞</h1>  
      <p>Correct answer. Love that for us 😌</p>  
      <p>Now please prepare for maximum romance + snacks + me being annoying (in a cute way).</p>  
      <p><strong>Happy Valentine’s Day, Kayt-Linn.</strong><br>— Jayden 💌</p>  
    </div>  
  </div>  
  
  <script>  
    const yesBtn = document.getElementById("yes");  
    const noBtn  = document.getElementById("no");  
    const tease  = document.getElementById("tease");  
    const buttons = document.getElementById("buttons");  
    const result = document.getElementById("result");  
  
    // iPhone-friendly tiny vibration (works in Safari if allowed)  
    function buzz(ms=20){  
      if (navigator.vibrate) navigator.vibrate(ms);  
    }  
  
    function confetti(){  
      const hearts = ["💖","💘","💗","💓","💞","💕"];  
      for (let i=0;i<90;i++){  
        const d = document.createElement("div");  
        d.className = "conf";  
        d.textContent = hearts[Math.floor(Math.random()*hearts.length)];  
        d.style.left = Math.random()*100 + "vw";  
        d.style.animationDuration = (2.2 + Math.random()*1.4) + "s";  
        d.style.transform = `translateY(0) rotate(${Math.random()*180}deg)`;  
        document.body.appendChild(d);  
        setTimeout(()=>d.remove(), 3600);  
      }  
    }  
  
    function sayYes(){  
      buzz(40);  
      buttons.classList.add("hidden");  
      tease.classList.add("hidden");  
      result.classList.remove("hidden");  
      confetti();  
    }  
  
    let noCount = 0;  
    const messages = [  
      "Nice try 😐",  
      "Kayt-Linn… be serious.",  
      "That’s literally not an option.",  
      "I will pretend I didn’t see that.",  
      "This is getting embarrassing (for the No button).",  
      "Alright. Enough. We’re switching to YES mode."  
    ];  
  
    function runAway(){  
      noCount++;  
      buzz(15);  
  
      // Update roast text  
      tease.textContent = messages[Math.min(noCount-1, messages.length-1)];  
  
      // Move button (works nicely on iPhone)  
      const x = (Math.random()*240 - 120);  
      const y = (Math.random()*220 - 110);  
      noBtn.style.transform = `translate(${x}px, ${y}px) rotate(${Math.random()*12 - 6}deg)`;  
  
      // Make it harder to tap over time  
      if (noCount >= 3) {  
        noBtn.style.filter = "blur(0.6px)";  
      }  
      if (noCount >= 4) {  
        noBtn.style.transform += " scale(0.92)";  
      }  
  
      // Final: convert to YES anyway  
      if (noCount >= 6) {  
        noBtn.textContent = "YES 💖";  
        noBtn.style.background = "var(--pink)";  
        noBtn.style.color = "white";  
        noBtn.style.filter = "none";  
        noBtn.onclick = sayYes;  
        tease.textContent = "Good. We fixed it ✅";  
      }  
    }  
  
    // Make "No" dodge even before click (extra funny on iPhone)  
    noBtn.addEventListener("touchstart", (e) => {  
      // If she tries to touch it, it runs  
      // Prevent accidental click on iOS  
      e.preventDefault();  
      runAway();  
    }, { passive: false });  
  
    noBtn.addEventListener("click", runAway);  
    yesBtn.addEventListener("click", sayYes);  
  </script>  
  
</body>  
</html>  
