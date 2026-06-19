<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Добро пожаловать!</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,700&family=Orbitron:wght@600;800&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
      background: #0a0a1a;
      padding: 1.5rem;
      position: relative;
      overflow-x: hidden;
    }

    .corner-signature {
      position: fixed;
      top: 12px;
      left: 16px;
      z-index: 20;
      font-family: 'Inter', 'Segoe UI', sans-serif;
      font-weight: 400;
      font-size: 0.7rem;
      color: rgba(255, 255, 255, 0.25);
      text-shadow: 0 0 6px rgba(200, 180, 255, 0.3);
      line-height: 1.5;
      letter-spacing: 0.3px;
      pointer-events: none;
      user-select: none;
      transition: color 0.4s ease, text-shadow 0.4s ease;
    }

    .corner-signature:hover {
      color: rgba(255, 255, 255, 0.5);
      text-shadow: 0 0 10px rgba(200, 180, 255, 0.6);
    }

    @media (max-width: 550px) {
      .corner-signature {
        font-size: 0.6rem;
        top: 8px;
        left: 10px;
      }
    }

    .space-background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      background: radial-gradient(ellipse at 30% 40%, #1a1030 0%, #030314 70%, #000010 100%);
      overflow: hidden;
    }

    .stars-layer-1 {
      position: absolute;
      width: 100%;
      height: 100%;
      background-image: 
        radial-gradient(1px 1px at 15px 70px, #ffffff, rgba(255,255,255,0)),
        radial-gradient(1px 1px at 85% 20%, #f8f0ff, rgba(255,255,255,0)),
        radial-gradient(1.5px 1.5px at 10% 80%, #c0d0ff, rgba(255,255,255,0)),
        radial-gradient(1px 1px at 50% 45%, #ffffff, rgba(255,255,255,0)),
        radial-gradient(1.2px 1.2px at 75% 65%, #e0e8ff, rgba(255,255,255,0)),
        radial-gradient(1px 1px at 30% 15%, #ffffff, rgba(255,255,255,0)),
        radial-gradient(1.3px 1.3px at 92% 75%, #bccaff, rgba(255,255,255,0)),
        radial-gradient(1px 1px at 22% 55%, #ffffff, rgba(255,255,255,0)),
        radial-gradient(1.4px 1.4px at 60% 85%, #d9e2ff, rgba(255,255,255,0)),
        radial-gradient(1px 1px at 5% 38%, #ffffff, rgba(255,255,255,0));
      background-size: 200px 200px;
      background-repeat: repeat;
      animation: subtleDrift 160s linear infinite;
      opacity: 0.9;
    }

    .stars-layer-2 {
      position: absolute;
      width: 100%;
      height: 100%;
      background-image: 
        radial-gradient(2px 2px at 20% 25%, #ffddaa, rgba(255,220,150,0)),
        radial-gradient(2.5px 2.5px at 70% 50%, #cce5ff, rgba(200,220,255,0)),
        radial-gradient(2px 2px at 45% 15%, #ffe9c7, rgba(255,230,180,0)),
        radial-gradient(3px 3px at 80% 10%, #b8d4ff, rgba(180,210,255,0)),
        radial-gradient(2px 2px at 12% 70%, #ffffff, rgba(255,255,255,0)),
        radial-gradient(2.2px 2.2px at 90% 40%, #fdd89c, rgba(255,200,140,0)),
        radial-gradient(2px 2px at 33% 80%, #dceaff, rgba(210,230,255,0)),
        radial-gradient(3px 3px at 55% 38%, #ffffff, rgba(255,255,255,0)),
        radial-gradient(2.3px 2.3px at 8% 12%, #ffdbb5, rgba(255,210,160,0));
      background-size: 350px 350px;
      background-repeat: repeat;
      animation: gentleFloat 200s linear infinite;
      opacity: 0.8;
    }

    .nebula {
      position: absolute;
      width: 100%;
      height: 100%;
      background: 
        radial-gradient(circle at 20% 30%, rgba(120, 80, 180, 0.2) 0%, transparent 50%),
        radial-gradient(circle at 80% 70%, rgba(60, 100, 200, 0.25) 0%, transparent 55%),
        radial-gradient(circle at 50% 90%, rgba(160, 120, 210, 0.15) 0%, transparent 45%),
        radial-gradient(circle at 10% 80%, rgba(70, 40, 130, 0.25) 0%, transparent 50%);
      filter: blur(45px);
      animation: nebulaPulse 18s ease-in-out infinite alternate;
    }

    .floating-texts {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: -1;
      pointer-events: none;
    }

    .floating-text {
      position: absolute;
      font-family: 'Orbitron', 'Inter', sans-serif;
      font-weight: 800;
      font-size: 1.8rem;
      color: rgba(255, 255, 255, 0.08);
      text-shadow: 0 0 15px rgba(255, 200, 0, 0.3), 0 0 40px rgba(255, 180, 0, 0.15);
      white-space: nowrap;
      animation: floatAcross var(--duration) linear infinite;
      animation-delay: var(--delay);
      user-select: none;
    }

    @keyframes floatAcross {
      0% {
        transform: translate(0, 0) rotate(var(--rotate));
        opacity: 0;
      }
      5% {
        opacity: 0.12;
      }
      50% {
        opacity: 0.15;
      }
      95% {
        opacity: 0.1;
      }
      100% {
        transform: translate(var(--moveX), var(--moveY)) rotate(var(--rotate));
        opacity: 0;
      }
    }

    @keyframes subtleDrift {
      0% { transform: translate(0, 0); }
      100% { transform: translate(-30px, 25px); }
    }

    @keyframes gentleFloat {
      0% { transform: translate(0, 0); }
      100% { transform: translate(40px, -15px); }
    }

    @keyframes nebulaPulse {
      0% { opacity: 0.7; transform: scale(1); }
      100% { opacity: 0.9; transform: scale(1.03); }
    }

    .cosmic-card {
      position: relative;
      z-index: 10;
      width: 100%;
      max-width: 800px;
      background: rgba(8, 12, 30, 0.55);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      border-radius: 3.5rem;
      padding: 3rem 2.5rem;
      box-shadow: 
        0 30px 60px rgba(0, 0, 0, 0.7),
        0 0 0 1px rgba(255, 255, 255, 0.12),
        inset 0 1px 0 rgba(255, 255, 255, 0.08);
      text-align: center;
      border: 1px solid rgba(180, 160, 255, 0.25);
      transition: transform 0.3s ease, box-shadow 0.4s ease;
      animation: cardAppear 1.2s cubic-bezier(0.23, 1, 0.32, 1) forwards;
    }

    .cosmic-card:hover {
      box-shadow: 0 40px 75px rgba(20, 10, 60, 0.8), 0 0 0 1px rgba(210, 190, 255, 0.3);
    }

    @keyframes cardAppear {
      0% {
        opacity: 0;
        transform: translateY(30px) scale(0.96);
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }

    .cosmic-card::before {
      content: "";
      position: absolute;
      inset: -2px;
      border-radius: inherit;
      padding: 2px;
      background: linear-gradient(135deg, rgba(180, 130, 255, 0.5), rgba(70, 130, 240, 0.4), rgba(200, 160, 255, 0.5));
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      pointer-events: none;
    }

    .welcome-title {
      font-family: 'Orbitron', 'Inter', sans-serif;
      font-weight: 800;
      font-size: clamp(2rem, 6vw, 3.2rem);
      letter-spacing: 0.03em;
      color: #ffffff;
      text-shadow: 
        0 0 12px rgba(180, 140, 255, 0.7),
        0 0 35px rgba(120, 60, 240, 0.5),
        0 0 70px rgba(80, 100, 255, 0.4);
      margin-bottom: 0.8rem;
      line-height: 1.2;
      word-break: break-word;
      animation: titleGlow 3s ease-in-out infinite alternate;
    }

    @keyframes titleGlow {
      0% {
        text-shadow: 0 0 12px rgba(180, 140, 255, 0.7), 0 0 35px rgba(120, 60, 240, 0.5), 0 0 70px rgba(80, 100, 255, 0.4);
      }
      100% {
        text-shadow: 0 0 20px rgba(200, 160, 255, 0.9), 0 0 50px rgba(140, 80, 255, 0.7), 0 0 90px rgba(100, 120, 255, 0.6);
      }
    }

    .small-description {
      font-size: 0.9rem;
      font-weight: 400;
      color: rgba(220, 215, 250, 0.9);
      margin-top: 1.2rem;
      letter-spacing: 0.3px;
      line-height: 1.6;
      background: rgba(20, 15, 45, 0.5);
      backdrop-filter: blur(6px);
      -webkit-backdrop-filter: blur(6px);
      display: inline-block;
      padding: 0.5rem 1.8rem;
      border-radius: 4rem;
      border: 1px solid rgba(210, 190, 255, 0.35);
      box-shadow: 0 8px 18px rgba(0, 0, 0, 0.4);
      max-width: 90%;
      margin-bottom: 1.8rem;
    }

    .btn-container {
      display: flex;
      justify-content: center;
      margin-top: 0.5rem;
    }

    .brawl-btn {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      font-family: 'Orbitron', 'Inter', sans-serif;
      font-weight: 700;
      font-size: 1.25rem;
      letter-spacing: 0.04em;
      text-decoration: none;
      color: #ffffff;
      padding: 1rem 2.8rem;
      border-radius: 4rem;
      border: 2px solid rgba(255, 200, 50, 0.6);
      box-shadow: 
        0 10px 30px rgba(255, 180, 0, 0.5),
        0 0 0 1px rgba(255, 255, 255, 0.2),
        inset 0 1px 0 rgba(255, 255, 255, 0.3);
      cursor: pointer;
      transition: all 0.35s ease;
      animation: pulseGlow 2.5s ease-in-out infinite;
      position: relative;
      overflow: hidden;
      background: linear-gradient(135deg, #ffaa00, #ff8800, #ffbb00);
      background-size: 200% auto;
      text-shadow: 0 2px 8px rgba(0, 0, 0, 0.8);
    }

    .brawl-btn::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(200, 120, 0, 0.3);
      border-radius: 4rem;
      z-index: 1;
      transition: background 0.35s ease;
    }

    .brawl-btn span {
      position: relative;
      z-index: 2;
    }

    .brawl-btn::after {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, transparent 60%);
      opacity: 0;
      transition: opacity 0.3s ease;
      z-index: 3;
      pointer-events: none;
    }

    .brawl-btn:hover {
      transform: translateY(-3px) scale(1.03);
      box-shadow: 
        0 18px 40px rgba(255, 180, 0, 0.7),
        0 0 0 1px rgba(255, 255, 255, 0.3),
        inset 0 1px 0 rgba(255, 255, 255, 0.4);
      border-color: rgba(255, 220, 100, 0.8);
      background: linear-gradient(135deg, #ffbb11, #ff9911, #ffcc22);
    }

    .brawl-btn:hover::before {
      background: rgba(180, 100, 0, 0.2);
    }

    .brawl-btn:hover::after {
      opacity: 1;
    }

    .brawl-btn:active {
      transform: translateY(0px) scale(0.98);
      box-shadow: 0 8px 20px rgba(255, 180, 0, 0.5);
    }

    @keyframes pulseGlow {
      0%, 100% {
        box-shadow: 0 10px 30px rgba(255, 180, 0, 0.5), 0 0 0 1px rgba(255, 255, 255, 0.2), inset 0 1px 0 rgba(255, 255, 255, 0.3);
      }
      50% {
        box-shadow: 0 14px 38px rgba(255, 200, 0, 0.75), 0 0 25px rgba(255, 200, 50, 0.5), 0 0 0 1px rgba(255, 255, 255, 0.3), inset 0 1px 0 rgba(255, 255, 255, 0.35);
      }
    }

    .btn-icon {
      font-size: 1.5rem;
      filter: drop-shadow(0 0 6px #ffffff);
    }

    @media (max-width: 550px) {
      .cosmic-card {
        padding: 2.5rem 1.5rem;
        border-radius: 2.8rem;
      }
      .welcome-title {
        font-size: clamp(1.6rem, 7vw, 2.4rem);
      }
      .small-description {
        font-size: 0.8rem;
        padding: 0.5rem 1.2rem;
      }
      .brawl-btn {
        font-size: 1.1rem;
        padding: 0.85rem 2.2rem;
      }
      .floating-text {
        font-size: 1.2rem;
      }
    }
  </style>
</head>
<body>
  <div class="corner-signature">
    Сайт сделан и запущен<br>
    "Касымов Ярослав Владиславович"<br>
    11 лет<br>
    Программист 3-й группы (прав HTML)
  </div>

  <div class="space-background">
    <div class="stars-layer-1"></div>
    <div class="stars-layer-2"></div>
    <div class="nebula"></div>
    
    <div class="floating-texts" id="floatingTexts"></div>
  </div>

  <main class="cosmic-card">
    <h1 class="welcome-title">Добро пожаловать!</h1>
    <p class="small-description">
      ✨ Это проект перехода на страницу Brawl Stars,<br>
      это не официально но я прошу переходить через этот,<br>
      если не сложно) 🎮
    </p>

    <div class="btn-container">
      <a href="https://play.google.com/store/apps/details/?id=com.supercell.brawlstars&hl=ru" target="_blank" rel="noopener noreferrer" class="brawl-btn">
        <span class="btn-icon">💥</span>
        <span>Скачать Brawl Stars</span>
        <span class="btn-icon">🏆</span>
      </a>
    </div>
  </main>

  <script>
    (function() {
      const container = document.getElementById('floatingTexts');
      const texts = ['Brawl Stars', 'Brawl Stars', 'Brawl Stars', 'Brawl Stars'];
      const count = 12;

      function createFloatingText(text, index) {
        const span = document.createElement('span');
        span.className = 'floating-text';
        span.textContent = text;

        const startX = Math.random() * 90;
        const startY = Math.random() * 90;
        const moveX = (Math.random() - 0.5) * 60;
        const moveY = (Math.random() - 0.5) * 60;
        const duration = 15 + Math.random() * 25;
        const delay = Math.random() * 20;
        const rotate = (Math.random() - 0.5) * 30;
        const fontSize = 1.2 + Math.random() * 2.5;

        span.style.setProperty('--moveX', moveX + 'vw');
        span.style.setProperty('--moveY', moveY + 'vh');
        span.style.setProperty('--duration', duration + 's');
        span.style.setProperty('--delay', delay + 's');
        span.style.setProperty('--rotate', rotate + 'deg');
        span.style.fontSize = fontSize + 'rem';
        span.style.left = startX + '%';
        span.style.top = startY + '%';

        if (index % 2 === 0) {
          span.style.color = 'rgba(255, 200, 0, 0.12)';
          span.style.textShadow = '0 0 20px rgba(255, 180, 0, 0.4), 0 0 50px rgba(255, 200, 50, 0.2)';
        } else {
          span.style.color = 'rgba(255, 220, 100, 0.1)';
          span.style.textShadow = '0 0 18px rgba(255, 200, 0, 0.3), 0 0 45px rgba(255, 180, 50, 0.15)';
        }

        return span;
      }

      for (let i = 0; i < count; i++) {
        const text = texts[i % texts.length];
        const floatingEl = createFloatingText(text, i);
        container.appendChild(floatingEl);
      }

      setInterval(() => {
        const allTexts = container.querySelectorAll('.floating-text');
        allTexts.forEach((el) => {
          const newStartX = Math.random() * 90;
          const newStartY = Math.random() * 90;
          const newMoveX = (Math.random() - 0.5) * 60;
          const newMoveY = (Math.random() - 0.5) * 60;
          const newDuration = 15 + Math.random() * 25;
          const newRotate = (Math.random() - 0.5) * 30;

          el.style.setProperty('--moveX', newMoveX + 'vw');
          el.style.setProperty('--moveY', newMoveY + 'vh');
          el.style.setProperty('--duration', newDuration + 's');
          el.style.setProperty('--rotate', newRotate + 'deg');
          el.style.left = newStartX + '%';
          el.style.top = newStartY + '%';
          
          el.style.animation = 'none';
          el.offsetHeight;
          el.style.animation = `floatAcross ${newDuration}s linear infinite`;
          el.style.animationDelay = '0s';
        });
      }, 20000);
    })();
  </script>
</body>
</html>
