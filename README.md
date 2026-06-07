<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>WANTED — Most Dangerous Criminal</title>
  <link href="https://fonts.googleapis.com/css2?family=Special+Elite&family=Rye&display=swap" rel="stylesheet"/>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'Special Elite', monospace;
      background: #c8a96e;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
      background-image:
        repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.03) 2px, rgba(0,0,0,0.03) 4px);
    }

    .poster {
      background: #f5e6c8;
      border: 8px double #5a3e1b;
      outline: 3px solid #5a3e1b;
      outline-offset: 4px;
      max-width: 500px;
      width: 100%;
      padding: 24px 28px 32px;
      text-align: center;
      box-shadow: 8px 8px 0 rgba(0,0,0,0.3), 16px 16px 0 rgba(0,0,0,0.15);
      position: relative;
      animation: paperIn 0.6s ease-out;
    }

    @keyframes paperIn {
      from { transform: scale(0.9) rotate(-2deg); opacity: 0; }
      to { transform: scale(1) rotate(0deg); opacity: 1; }
    }

    .poster::before {
      content: '';
      position: absolute;
      inset: 8px;
      border: 2px solid #5a3e1b;
      opacity: 0.3;
      pointer-events: none;
    }

    .reward-top {
      font-family: 'Rye', serif;
      font-size: 13px;
      letter-spacing: 4px;
      color: #5a3e1b;
      margin-bottom: 4px;
      text-transform: uppercase;
    }

    .wanted-title {
      font-family: 'Rye', serif;
      font-size: 52px;
      color: #1a0a00;
      line-height: 1;
      margin: 0;
      text-shadow: 3px 3px 0 rgba(90,62,27,0.4);
      letter-spacing: 2px;
    }

    .dead-or-alive {
      font-size: 14px;
      letter-spacing: 6px;
      color: #8b1a1a;
      border-top: 2px solid #5a3e1b;
      border-bottom: 2px solid #5a3e1b;
      padding: 4px 0;
      margin: 10px 0;
      text-transform: uppercase;
      font-weight: bold;
    }

    .photo-area {
      width: 220px;
      height: 270px;
      background: #d4bfa0;
      border: 4px solid #5a3e1b;
      margin: 14px auto;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      position: relative;
      overflow: hidden;
    }

    .photo-area img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: sepia(40%) contrast(1.1);
    }

    .reveal-overlay {
      position: absolute;
      inset: 0;
      background: #1a0a00;
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 10;
    }

    .flicker-text {
      color: #f5e6c8;
      font-family: 'Rye', serif;
      font-size: 22px;
      text-align: center;
      letter-spacing: 2px;
    }

    .corner-stars {
      position: absolute;
      font-size: 18px;
      color: #5a3e1b;
      opacity: 0.6;
    }
    .cs-tl { top: 12px; left: 12px; }
    .cs-tr { top: 12px; right: 12px; }
    .cs-bl { bottom: 12px; left: 12px; }
    .cs-br { bottom: 12px; right: 12px; }

    .criminal-name {
      font-family: 'Rye', serif;
      font-size: 26px;
      color: #1a0a00;
      margin: 6px 0 2px;
      letter-spacing: 1px;
    }

    .aka {
      font-size: 12px;
      color: #5a3e1b;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 10px;
    }

    .crimes-list {
      text-align: left;
      border-top: 1px dashed #5a3e1b;
      border-bottom: 1px dashed #5a3e1b;
      padding: 8px 0;
      margin: 10px 0;
      font-size: 13px;
      color: #3a2005;
      line-height: 1.8;
    }

    .crime-item { display: flex; gap: 8px; }

    .bounty-section { margin-top: 14px; }

    .bounty-label {
      font-size: 13px;
      letter-spacing: 5px;
      color: #5a3e1b;
      text-transform: uppercase;
    }

    .bounty-amount {
      font-family: 'Rye', serif;
      font-size: 42px;
      color: #8b1a1a;
      line-height: 1;
      text-shadow: 2px 2px 0 rgba(139,26,26,0.3);
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.04); }
    }

    .bounty-sub {
      font-size: 11px;
      color: #5a3e1b;
      letter-spacing: 2px;
      margin-top: 2px;
    }

    .upload-btn {
      display: inline-block;
      margin-top: 18px;
      background: #8b1a1a;
      color: #f5e6c8;
      border: 3px solid #5a3e1b;
      font-family: 'Special Elite', monospace;
      font-size: 13px;
      letter-spacing: 3px;
      padding: 10px 24px;
      cursor: pointer;
      text-transform: uppercase;
      transition: all 0.2s;
    }

    .upload-btn:hover { background: #6b1212; transform: scale(1.03); }
    .upload-btn:active { transform: scale(0.97); }

    .footer-text {
      font-size: 10px;
      color: #5a3e1b;
      letter-spacing: 2px;
      margin-top: 16px;
      opacity: 0.7;
    }

    .name-input, .crime-input {
      background: transparent;
      border: none;
      border-bottom: 2px dashed #5a3e1b;
      font-family: 'Rye', serif;
      font-size: 22px;
      color: #1a0a00;
      text-align: center;
      width: 90%;
      outline: none;
      padding: 4px 0;
    }

    .crime-input {
      font-family: 'Special Elite', monospace;
      font-size: 12px;
      width: 100%;
      margin: 2px 0;
      border-bottom: 1px dashed #5a3e1b;
      color: #3a2005;
    }

    .edit-hint {
      font-size: 10px;
      color: #5a3e1b;
      opacity: 0.6;
      margin-bottom: 2px;
      letter-spacing: 1px;
    }

    #fileInput { display: none; }
  </style>
</head>
<body>

<div class="poster">
  <span class="corner-stars cs-tl">✦</span>
  <span class="corner-stars cs-tr">✦</span>
  <span class="corner-stars cs-bl">✦</span>
  <span class="corner-stars cs-br">✦</span>

  <div class="reward-top">— The Law Demands —</div>
  <h1 class="wanted-title">WANTED</h1>
  <div class="dead-or-alive">Dead or Alive</div>

  <!-- ✅ FIXED PHOTO - apni photo ka naam yahan likho -->
  <div class="photo-area">
    <div class="reveal-overlay" id="revealOverlay">
      <div class="flicker-text">REVEALING<br>IDENTITY...</div>
    </div>
    <img id="criminalPhoto" src="photo.jpg" alt="Criminal Photo" />
  </div>

  <!-- ✅ CHANGE PHOTO BUTTON -->
  <input type="file" id="fileInput" accept="image/*" onchange="handlePhoto(event)" />
  <button class="upload-btn" onclick="document.getElementById('fileInput').click()">
    🔄 Change Photo
  </button>

  <p class="edit-hint" style="margin-top:12px;">✎ Click to edit name</p>
  <div class="criminal-name">
    <input class="name-input" type="text" placeholder="CRIMINAL NAME" value="FORDO" maxlength="25" />
  </div>
  <div class="aka">A.K.A. "The Notorious One"</div>

  <div class="crimes-list">
    <p class="edit-hint" style="margin-bottom:4px;">✎ Click crimes to edit</p>
    <div class="crime-item">🔫 <input class="crime-input" value="Ate the last samosa without asking" /></div>
    <div class="crime-item">🎯 <input class="crime-input" value="Replied 'k' to a 3-paragraph message" /></div>
    <div class="crime-item">💀 <input class="crime-input" value="Finishes Netflix shows alone first" /></div>
  </div>

  <div class="bounty-section">
    <div class="bounty-label">Reward</div>
    <div class="bounty-amount">₹1,00,000</div>
    <div class="bounty-sub">One Lakh Rupees — No Questions Asked</div>
  </div>

  <div class="footer-text">
    Issued by: The Society of Betrayed Friends &nbsp;|&nbsp; Est. 2025
  </div>
</div>

<script>
  function handlePhoto(event) {
    const file = event.target.files[0];
    if (!file) return;

    const reader = new FileReader();
    reader.onload = function(e) {
      const overlay = document.getElementById('revealOverlay');
      const img = document.getElementById('criminalPhoto');

      overlay.style.display = 'flex';

      let count = 0;
      const flicker = setInterval(() => {
        overlay.style.opacity = count % 2 === 0 ? '0' : '1';
        count++;
        if (count > 9) {
          clearInterval(flicker);
          overlay.style.opacity = '1';
          img.src = e.target.result;

          setTimeout(() => {
            let fade = 0;
            const fadeOut = setInterval(() => {
              overlay.style.opacity = fade % 2 === 0 ? '0' : '0.8';
              fade++;
              if (fade > 11) {
                clearInterval(fadeOut);
                overlay.style.display = 'none';
              }
            }, 100);
          }, 400);
        }
      }, 100);
    };
    reader.readAsDataURL(file);
  }
</script>

</body>
</html>
