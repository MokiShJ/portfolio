<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>EEE Engineer Portfolio- Electric Pulse Cursor</title>
  <style>
    /* Reset and base styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
      height: 100vh;
      overflow-x: hidden;
      background: #000000;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center; 
      text-align: center;
      padding: 40px 20px;
      cursor: none; /* Hide default cursor */
      position: relative;
      user-select: none;
    }

    /* Particle background canvas */
    #particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
      z-index: 0;
      background: transparent;
    }

    h1 {
      font-size: 3rem;
      color: #fff;
      text-shadow: 0 0 12px #ffff00aa, 0 0 30px #ffff0077;
      margin-bottom: 25px;
      font-weight: 700;
      letter-spacing: 1.5px;
      z-index: 10;
      position: relative;
    }

    p {
      max-width: 700px;
      font-size: 1.25rem;
      line-height: 1.7;
      color: #ddd;
      text-shadow: 0 0 6px #ffff0077;
      margin-bottom: 50px;
      position: relative;
      z-index: 10;
    }

    .cards {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
      max-width: 900px;
      z-index: 10;
      position: relative;
    }

    .card {
      background: rgba(255, 255, 255, 0.08);
      border-radius: 15px;
      padding: 18px 32px;
      min-width: 180px;
      color: #ffff99;
      font-weight: 600;
      font-size: 1.1rem;
      box-shadow: 0 0 15px #ffff0099;
      cursor: default;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      user-select: none;
      letter-spacing: 0.8px;
      backdrop-filter: blur(5px);
      border: 1.5px solid #ffff0040;
      text-transform: uppercase;
    }

    .card:hover {
      transform: translateY(-6px) scale(1.05);
      box-shadow: 0 0 30px #ffff00cc, 0 0 40px #ffff00cc;
    }

    .fun-facts {
      margin-top: 60px;
      color: #ffff33;
      font-size: 1.5rem;
      z-index: 10;
      position: relative;
      text-align: center;
      max-width: 650px;
      margin-left: auto;
      margin-right: auto;
      user-select: none;
    }

    .fun-facts h2 {
      font-size: 2rem;
      margin-bottom: 15px;
      text-shadow: 0 0 18px #ffff00dd;
      animation: pulse 3s infinite;
    }

    .fun-facts p {
      font-weight: 500;
      font-style: italic;
      text-shadow: 0 0 12px #ffff0077;
      transition: opacity 0.5s ease-in-out;
      min-height: 4rem;
    }

    @keyframes pulse {
      0%, 100% {
        text-shadow: 0 0 12px #ffff00dd;
      }
      50% {
        text-shadow: 0 0 28px #ffff00ff;
      }
    }

    /* Electric pulse cursor container */
    #cursor {
      position: fixed;
      top: 0;
      left: 0;
      width: 40px;
      height: 40px;
      pointer-events: none;
      z-index: 9999;
      user-select: none;
      transform-origin: center;
      will-change: transform, left, top;
    }

    /* Outer glowing ring */
    #cursor .outer-ring {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 40px;
      height: 40px;
      border: 2.5px solid #ffff00cc;
      border-radius: 50%;
      transform: translate(-50%, -50%);
      animation: pulseRing 1.8s ease-out infinite;
      box-shadow: 0 0 20px 6px #ffff00aa;
      opacity: 0.6;
    }

    /* Inner glowing core */
    #cursor .inner-core {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 12px;
      height: 12px;
      background: #ffff44;
      border-radius: 50%;
      transform: translate(-50%, -50%);
      box-shadow:
        0 0 6px 3px #ffff55,
        0 0 14px 5px #ffff77;
      animation: corePulse 1.8s ease-in-out infinite;
      opacity: 0.9;
    }

    @keyframes pulseRing {
      0% {
        transform: translate(-50%, -50%) scale(0.8);
        opacity: 0.6;
        box-shadow: 0 0 15px 4px #ffff00aa;
      }
      50% {
        transform: translate(-50%, -50%) scale(1.3);
        opacity: 0.1;
        box-shadow: 0 0 30px 10px #ffff00cc;
      }
      100% {
        transform: translate(-50%, -50%) scale(0.8);
        opacity: 0.6;
        box-shadow: 0 0 15px 4px #ffff00aa;
      }
    }

    @keyframes corePulse {
      0%, 100% {
        transform: translate(-50%, -50%) scale(1);
        opacity: 0.9;
        box-shadow:
          0 0 6px 3px #ffff55,
          0 0 14px 5px #ffff77;
      }
      50% {
        transform: translate(-50%, -50%) scale(1.15);
        opacity: 1;
        box-shadow:
          0 0 10px 5px #ffffee,
          0 0 22px 10px #ffffaa;
      }
    }

    /* Spark particles */
    .spark {
      position: fixed;
      width: 6px;
      height: 6px;
      background: #ffff66;
      border-radius: 50%;
      box-shadow: 0 0 10px 3px #ffff99;
      pointer-events: none;
      z-index: 9998;
      opacity: 1;
      animation: sparkFade 0.8s forwards;
      filter: drop-shadow(0 0 8px #ffff99);
      will-change: transform, opacity;
    }

    @keyframes sparkFade {
      to {
        opacity: 0;
        transform: translateY(-15px) scale(0.3);
      }
    }
  </style>
</head>
<body>
  <canvas id="particles"></canvas>

  <div id="cursor" aria-hidden="true">
    <div class="outer-ring"></div>
    <div class="inner-core"></div>
  </div>

  <h1>I'm Mokish Jayaraman</h1>
  <p>
    Passionate about Electrical and Electronics Engineering, innovating embedded systems, automation, and power electronics for real-world impact.
  </p>

  <div class="cards" role="list" aria-label="Skills">
    <div class="card" role="listitem">Embedded Systems</div>
    <div class="card" role="listitem">IoT & Automation</div>
    <div class="card" role="listitem">Power Electronics</div>
    <div class="card" role="listitem">MATLAB & Simulation</div>
    <div class="card" role="listitem">Arduino & Microcontrollers</div>
    <div class="card" role="listitem">Circuit Design</div>
  </div>

  <section class="fun-facts" aria-live="polite">
    <h2>Do You Know?</h2>
    <p id="fact">
      1st Runner-Up – Paper Presentation, Smart Car Parking System
    </p>
  </section>

  <script>
    // Setup particle background (floating electric sparks)
    const canvas = document.getElementById('particles');
    const ctx = canvas.getContext('2d');
    let particles = [];
    const maxParticles = 60;

    class Spark {
      constructor() {
        this.reset();
      }
      reset() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 7 + 6;
        this.speedX = (Math.random() - 0.5) * 0.3;
        this.speedY = (Math.random() - 0.5) * 0.15;
        this.opacity = Math.random() * 0.5 + 0.4;
        this.rotation = Math.random() * 2 * Math.PI;
        this.rotationSpeed = (Math.random() - 0.5) * 0.02;
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        this.rotation += this.rotationSpeed;
        if (this.x < -this.size) this.x = canvas.width + this.size;
        if (this.x > canvas.width + this.size) this.x = -this.size;
        if (this.y < -this.size) this.y = canvas.height + this.size;
        if (this.y > canvas.height + this.size) this.y = -this.size;
      }
      draw() {
        ctx.save();
        ctx.translate(this.x, this.y);
        ctx.rotate(this.rotation);
        ctx.beginPath();
        ctx.moveTo(0, -this.size * 0.4);
        ctx.lineTo(this.size * 0.15, 0);
        ctx.lineTo(0, 0);
        ctx.lineTo(this.size * 0.15, this.size * 0.4);
        ctx.lineTo(-this.size * 0.2, 0);
        ctx.lineTo(0, 0);
        ctx.closePath();
        const gradient = ctx.createRadialGradient(0, 0, this.size * 0.1, 0, 0, this.size);
        gradient.addColorStop(0, `rgba(255, 255, 0, ${this.opacity})`);
        gradient.addColorStop(1, 'rgba(255, 255, 0, 0)');
        ctx.fillStyle = gradient;
        ctx.shadowColor = 'rgba(255, 255, 0, 0.8)';
        ctx.shadowBlur = 8;
        ctx.fill();
        ctx.restore();
      }
    }

    function initParticles() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      particles = [];
      for (let i = 0; i < maxParticles; i++) {
        particles.push(new Spark());
      }
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animateParticles);
    }

    window.addEventListener('resize', initParticles);

    initParticles();
    animateParticles();

    // Custom electric pulse cursor logic
    const cursor = document.getElementById('cursor');

    // Create spark elements that follow the cursor briefly
    function createSpark(x, y) {
      const spark = document.createElement('div');
      spark.className = 'spark';
      document.body.appendChild(spark);
      spark.style.left = `${x}px`;
      spark.style.top = `${y}px`;

      setTimeout(() => {
        spark.remove();
      }, 800);
    }

    window.addEventListener('mousemove', e => {
      cursor.style.left = `${e.clientX}px`;
      cursor.style.top = `${e.clientY}px`;

      // Random chance to create spark for performance balance
      if (Math.random() < 0.3) {
        createSpark(e.clientX + (Math.random() * 20 - 10), e.clientY + (Math.random() * 20 - 10));
      }
    });

    // Cycle through your personal info facts every 3 seconds with fade animation
    const facts = [
      "1st Runner-Up – Paper Presentation, Smart Car Parking System",
      "Patent has been filed for one of my projects.",
      "NPTEL – Cloud Computing, Renewable Energy",
      "HackerRank – CSS, JavaScript, SQL (Basic & Advanced), Problem Solving Techniques.",
      "Won prizes for project presentations at college and tech fest"
    ];

    const factElement = document.getElementById('fact');
    let factIndex = 0;

    function showNextFact() {
      factIndex = (factIndex + 1) % facts.length;
      factElement.style.opacity = 0;

      setTimeout(() => {
        factElement.textContent = facts[factIndex];
        factElement.style.opacity = 1;
      }, 600); // fade duration
    }

    setInterval(showNextFact, 3000);
  </script>
</body>
</html>
