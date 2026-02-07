<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1"/>
  <title>A Small Birthday Note 🤍</title>
  <style>
    :root {
      --bg: #07090f;
      --card: rgba(255,255,255,.08);
      --card2: rgba(255,255,255,.12);
      --txt: rgba(255,255,255,.92);
      --muted: rgba(255,255,255,.70);
      --ring: rgba(255,255,255,.18);
      --shadow: rgba(0,0,0,.45);
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      min-height: 100vh;
      display: grid;
      place-items: center;
      background: radial-gradient(1000px 600px at 50% 20%, rgba(255,255,255,.08), transparent 55%),
                  radial-gradient(700px 500px at 20% 80%, rgba(255,255,255,.06), transparent 60%),
                  var(--bg);
      color: var(--txt);
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      overflow: hidden;
    }
    .wrap {
      width: min(920px, 92vw);
      padding: 18px;
      position: relative;
      z-index: 2;
    }
    .topbar {
      display:flex;
      gap:10px;
      align-items:center;
      justify-content:space-between;
      margin-bottom: 14px;
      opacity: .95;
    }
    .pill {
      border: 1px solid var(--ring);
      background: rgba(255,255,255,.06);
      border-radius: 999px;
      padding: 8px 12px;
      font-size: 13px;
      color: var(--muted);
      display: inline-flex;
      gap: 8px;
      align-items: center;
      user-select: none;
      backdrop-filter: blur(8px);
    }
    .pill b { color: var(--txt); font-weight: 650; }
    .grid {
      display:grid;
      grid-template-columns: 1.05fr .95fr;
      gap: 16px;
    }
    @media (max-width: 860px) {
      .grid { grid-template-columns: 1fr; }
    }

    .card {
      background: linear-gradient(180deg, var(--card), rgba(255,255,255,.04));
      border: 1px solid var(--ring);
      border-radius: 22px;
      box-shadow: 0 18px 70px var(--shadow);
      backdrop-filter: blur(10px);
      overflow: hidden;
    }

    /* Envelope */
    .envelopeArea {
      padding: 18px;
      display:flex;
      flex-direction: column;
      gap: 12px;
    }
    .envelope {
      height: 340px;
      position: relative;
      border-radius: 18px;
      background: linear-gradient(135deg, rgba(255,255,255,.08), rgba(255,255,255,.03));
      border: 1px solid var(--ring);
      display:grid;
      place-items:center;
      overflow: hidden;
    }
    .env-inner {
      width: min(520px, 92%);
      height: 250px;
      position: relative;
      transform-style: preserve-3d;
    }
    .env-back {
      position:absolute; inset:0;
      border-radius: 18px;
      background: linear-gradient(180deg, rgba(255,255,255,.10), rgba(255,255,255,.04));
      border: 1px solid rgba(255,255,255,.16);
      box-shadow: inset 0 0 0 1px rgba(255,255,255,.06);
    }
    .env-front {
      position:absolute; inset:0;
      border-radius: 18px;
      background: linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
      border: 1px solid rgba(255,255,255,.12);
      clip-path: polygon(0 38%, 50% 78%, 100% 38%, 100% 100%, 0 100%);
    }
    .env-flap {
      position:absolute; inset:0;
      border-radius: 18px;
      background: linear-gradient(180deg, rgba(255,255,255,.14), rgba(255,255,255,.05));
      border: 1px solid rgba(255,255,255,.18);
      clip-path: polygon(0 38%, 50% 0, 100% 38%, 50% 76%);
      transform-origin: 50% 38%;
      transform: rotateX(0deg);
      transition: transform .8s ease;
      filter: drop-shadow(0 10px 18px rgba(0,0,0,.35));
    }
    .seal {
      position:absolute;
      left: 50%; top: 58%;
      transform: translate(-50%, -50%);
      width: 64px; height: 64px;
      border-radius: 999px;
      background: radial-gradient(circle at 30% 30%, rgba(255,255,255,.35), rgba(255,255,255,.10) 40%, rgba(255,255,255,.06));
      border: 1px solid rgba(255,255,255,.18);
      display:grid;
      place-items:center;
      font-weight: 750;
      letter-spacing: .5px;
      color: rgba(255,255,255,.85);
      box-shadow: 0 16px 35px rgba(0,0,0,.35);
      user-select: none;
      transition: transform .3s ease, opacity .3s ease;
    }
    .letter {
      position:absolute;
      left: 50%;
      top: 58%;
      transform: translate(-50%, -50%);
      width: 92%;
      height: 84%;
      border-radius: 16px;
      background: linear-gradient(180deg, rgba(255,255,255,.14), rgba(255,255,255,.06));
      border: 1px solid rgba(255,255,255,.18);
      box-shadow: 0 18px 60px rgba(0,0,0,.45);
      padding: 16px 16px 14px;
      opacity: 0;
      transform: translate(-50%, -20%) scale(.96);
      transition: opacity .4s ease, transform .8s ease;
      overflow: hidden;
    }
    .letter h2 {
      margin: 0 0 8px 0;
      font-size: 18px;
      letter-spacing: .3px;
      display:flex;
      align-items:center;
      gap:10px;
    }
    .letter h2 .dot {
      width: 8px; height:8px; border-radius: 999px;
      background: rgba(255,255,255,.7);
      box-shadow: 0 0 0 6px rgba(255,255,255,.08);
    }
    .letter p {
      margin: 0;
      color: rgba(255,255,255,.84);
      line-height: 1.55;
      font-size: 14.5px;
      white-space: pre-wrap;
    }
    .typeCursor {
      display:inline-block;
      width: 8px;
      height: 16px;
      margin-left: 2px;
      background: rgba(255,255,255,.65);
      vertical-align: -2px;
      animation: blink .9s infinite;
    }
    @keyframes blink { 0%,49%{opacity:1} 50%,100%{opacity:.1} }

    .opened .env-flap { transform: rotateX(150deg); }
    .opened .seal { opacity: 0; transform: translate(-50%, -50%) scale(.85); }
    .opened .letter { opacity: 1; transform: translate(-50%, -50%) scale(1); }

    /* Controls */
    .controls {
      display:flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items:center;
      justify-content: space-between;
    }
    .btns { display:flex; gap:10px; flex-wrap: wrap; }
    button {
      border: 1px solid rgba(255,255,255,.18);
      background: rgba(255,255,255,.08);
      color: var(--txt);
      padding: 10px 12px;
      border-radius: 14px;
      font-weight: 650;
      cursor: pointer;
      transition: transform .06s ease, background .2s ease, border-color .2s ease;
      user-select:none;
      box-shadow: 0 12px 30px rgba(0,0,0,.35);
    }
    button:active { transform: translateY(1px); }
    button:hover { background: rgba(255,255,255,.12); border-color: rgba(255,255,255,.28); }

    .mini {
      font-size: 12px;
      color: var(--muted);
      display:flex;
      gap:10px;
      align-items:center;
    }
    .switch {
      display:inline-flex;
      align-items:center;
      gap:8px;
      padding: 8px 10px;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,.14);
      background: rgba(255,255,255,.06);
    }
    .switch input { accent-color: white; }

    /* Right side: personalizer */
    .panel {
      padding: 18px;
      display:flex;
      flex-direction: column;
      gap: 12px;
    }
    .panel h3 { margin: 0; font-size: 16px; letter-spacing: .2px; }
    label { font-size: 13px; color: var(--muted); }
    input, textarea {
      width: 100%;
      border-radius: 14px;
      border: 1px solid rgba(255,255,255,.16);
      background: rgba(255,255,255,.06);
      color: var(--txt);
      padding: 10px 12px;
      outline: none;
    }
    textarea { min-height: 160px; resize: vertical; line-height: 1.4; }
    .hint {
      font-size: 12px;
      color: rgba(255,255,255,.60);
      line-height: 1.4;
    }

    /* Floating particles */
    .floatLayer {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 1;
    }
    .particle {
      position:absolute;
      font-size: 18px;
      opacity: .0;
      transform: translate(-50%,-50%) scale(.8);
      animation: rise 1.8s ease forwards;
      filter: drop-shadow(0 10px 16px rgba(0,0,0,.35));
    }
    @keyframes rise {
      0%   { opacity: 0; transform: translate(-50%,-50%) scale(.8); }
      15%  { opacity: .9; }
      100% { opacity: 0; transform: translate(-50%,-140px) scale(1.1); }
    }
    .footerNote {
      margin-top: 8px;
      font-size: 12px;
      color: rgba(255,255,255,.55);
    }
    .kbd {
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
      font-size: 11px;
      padding: 2px 6px;
      border-radius: 8px;
      border: 1px solid rgba(255,255,255,.16);
      background: rgba(255,255,255,.06);
      color: rgba(255,255,255,.75);
    }
  </style>
</head>

<body>
  <div class="floatLayer" id="floatLayer"></div>

  <div class="wrap">
    <div class="topbar">
      <div class="pill">💌 <b>Interactive Birthday Note</b> — open the envelope</div>
      <div class="pill">Tip: press <span class="kbd">Space</span> to open/close</div>
    </div>

    <div class="grid">
      <!-- Left: Envelope + Note -->
      <div class="card envelopeArea">
        <div class="envelope" id="envelope">
          <div class="env-inner" id="envInner">
            <div class="env-back"></div>
            <div class="letter" id="letter">
              <h2><span class="dot"></span><span id="toLine">To: My Love 🤍</span></h2>
              <p id="typed"></p><span class="typeCursor" id="cursor"></span>
            </div>
            <div class="env-front"></div>
            <div class="env-flap"></div>
            <div class="seal" id="seal">بسم</div>
          </div>
        </div>

        <div class="controls">
          <div class="btns">
            <button id="openBtn">Open / Close</button>
            <button id="sparkleBtn">Send Duʿāʾ ✨</button>
            <button id="copyBtn">Copy Note</button>
          </div>
          <div class="mini">
            <span class="switch">
              <input type="checkbox" id="typingToggle" checked>
              <label for="typingToggle" style="cursor:pointer;color:rgba(255,255,255,.75)">Typing effect</label>
            </span>
          </div>
        </div>

        <div class="footerNote">
          Personalize on the right, then open the envelope. (Good for GitHub Pages as <span class="kbd">index.html</span>)
        </div>
      </div>

      <!-- Right: Personalizer -->
      <div class="card panel">
        <h3>Personalize the note</h3>

        <div>
          <label>Her name / nickname</label>
          <input id="herName" placeholder="e.g., Aisyah / Sayang / Love" value="My Love 🤍"/>
        </div>

        <div>
          <label>Your name (signature)</label>
          <input id="yourName" placeholder="e.g., Ariff" value="From: Someone who prays for you"/>
        </div>

        <div>
          <label>Your message (editable)</label>
          <textarea id="messageBox"></textarea>
          <div class="hint">
            Keep it respectful + duʿāʾ-based if you want a modest Muslim tone. You can mention exams, goals, barakah, and ease.
          </div>
        </div>

        <div class="btns">
          <button id="applyBtn">Apply Message</button>
          <button id="resetBtn">Reset Default</button>
        </div>
      </div>
    </div>
  </div>

<script>
  const envelope = document.getElementById("envelope");
  const openBtn = document.getElementById("openBtn");
  const sparkleBtn = document.getElementById("sparkleBtn");
  const copyBtn = document.getElementById("copyBtn");
  const applyBtn = document.getElementById("applyBtn");
  const resetBtn = document.getElementById("resetBtn");
  const typingToggle = document.getElementById("typingToggle");

  const toLine = document.getElementById("toLine");
  const typed = document.getElementById("typed");
  const cursor = document.getElementById("cursor");
  const floatLayer = document.getElementById("floatLayer");

  const herName = document.getElementById("herName");
  const yourName = document.getElementById("yourName");
  const messageBox = document.getElementById("messageBox");

  const defaultMsg =
`Bismillāh.

Happy birthday 🤍

On your birthday, I don’t ask for anything grand —
I ask Allah to protect your heart, ease your worries,
and guide every step you take.

May He grant you health when you are tired,
peace when life feels heavy,
and strength when you doubt yourself.

And for your exams: may Allah place barakah in your time,
make your understanding clear, and make your effort count.
May you walk into the exam hall calm, focused, and confident.

I’m grateful for you, today and always.
May Allah keep you under His care and fill your year with goodness.

Āmīn.

— (signature)`;

  let fullText = defaultMsg.replace("(signature)", yourName.value || "From me");
  let typingTimer = null;
  let isOpen = false;

  function setMessageFromInputs() {
    const to = herName.value?.trim() || "My Love 🤍";
    toLine.textContent = "To: " + to;

    const sign = yourName.value?.trim() || "From me";
    const raw = messageBox.value || defaultMsg;
    fullText = raw.replace("(signature)", sign);

    // If already open, refresh display
    if (isOpen) renderText();
  }

  function renderText() {
    clearInterval(typingTimer);
    typed.textContent = "";
    cursor.style.display = "inline-block";

    if (!typingToggle.checked) {
      typed.textContent = fullText;
      cursor.style.display = "none";
      return;
    }

    let i = 0;
    typingTimer = setInterval(() => {
      typed.textContent += fullText[i] || "";
      i++;
      if (i >= fullText.length) {
        clearInterval(typingTimer);
        cursor.style.display = "none";
      }
    }, 16);
  }

  function toggleEnvelope() {
    isOpen = !isOpen;
    envelope.classList.toggle("opened", isOpen);
    if (isOpen) {
      renderText();
      burst("🤍", 10);
    } else {
      clearInterval(typingTimer);
      typed.textContent = "";
      cursor.style.display = "inline-block";
    }
  }

  function burst(symbol, count = 12) {
    const rect = envelope.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;

    for (let i = 0; i < count; i++) {
      const p = document.createElement("div");
      p.className = "particle";
      p.textContent = Math.random() < 0.5 ? symbol : "✨";
      p.style.left = (cx + (Math.random() - 0.5) * 220) + "px";
      p.style.top  = (cy + (Math.random() - 0.5) * 120) + "px";
      p.style.fontSize = (14 + Math.random() * 16) + "px";
      p.style.animationDuration = (1.3 + Math.random() * 1.1) + "s";
      floatLayer.appendChild(p);
      setTimeout(() => p.remove(), 2200);
    }
  }

  function copyNote() {
    const to = herName.value?.trim() || "My Love 🤍";
    const compiled = `To: ${to}\n\n${fullText}`;
    navigator.clipboard.writeText(compiled).then(() => {
      burst("✅", 10);
    }).catch(() => {
      // fallback if clipboard blocked
      prompt("Copy this:", compiled);
    });
  }

  // Default fill
  messageBox.value = defaultMsg;
  setMessageFromInputs();

  // Events
  openBtn.addEventListener("click", toggleEnvelope);
  document.getElementById("seal").addEventListener("click", toggleEnvelope);

  sparkleBtn.addEventListener("click", () => {
    burst("✨", 18);
    if (!isOpen) toggleEnvelope();
  });

  copyBtn.addEventListener("click", copyNote);

  applyBtn.addEventListener("click", () => {
    setMessageFromInputs();
    burst("✨", 12);
  });

  resetBtn.addEventListener("click", () => {
    herName.value = "My Love 🤍";
    yourName.value = "From: Someone who prays for you";
    messageBox.value = defaultMsg;
    setMessageFromInputs();
    burst("🤍", 12);
  });

  typingToggle.addEventListener("change", () => {
    if (isOpen) renderText();
  });

  // Keyboard: Space toggles open/close
  window.addEventListener("keydown", (e) => {
    if (e.code === "Space") {
      e.preventDefault();
      toggleEnvelope();
    }
  });

  // Click anywhere on envelope to sparkle
  envelope.addEventListener("click", (e) => {
    // avoid double-trigger on seal/open btn
    if (e.target.id === "openBtn" || e.target.id === "seal") return;
    burst("🤍", 8);
  });
</script>
</body>
</html>
# HBLOML
