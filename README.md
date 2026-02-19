<html lang="te">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Ugadi Greeting</title>
    <style>
        :root { --saffron: #FF9933; --gold: #FFD700; --maroon: #800000; }
        body { margin: 0; font-family: 'Arial', sans-serif; overflow: hidden; background: #FFF8E1; text-align: center; }
        
        /* Toran (Garland) at the top */
        .toran { position: fixed; top: 0; width: 100%; font-size: 30px; letter-spacing: -5px; z-index: 10; background: rgba(255,255,255,0.2); }

        .page { height: 100vh; width: 100vw; position: absolute; transition: transform 1s cubic-bezier(0.645, 0.045, 0.355, 1); display: flex; flex-direction: column; align-items: center; justify-content: center; }
        #page2 { transform: translateY(100%); background: radial-gradient(circle, #fff9c4, #ffecb3); }

        /* Temple Styling */
        .temple-container { position: relative; perspective: 1000px; }
        .temple { font-size: 200px; filter: drop-shadow(0 0 20px rgba(255, 153, 51, 0.5)); animation: glow 3s ease-in-out infinite alternate; z-index: 5; position: relative; }
        
        /* Flying Bird Path */
        .bird-fly { position: absolute; font-size: 40px; animation: flyPath 12s linear infinite; z-index: 6; }

        /* Interactive Bell */
        .bell-box { margin: 20px; cursor: pointer; display: inline-block; transition: 0.3s; }
        .bell-btn { font-size: 60px; display: inline-block; }
        .bell-ring { animation: ring 0.5s ease-in-out infinite alternate; }

        /* Falling Items */
        .falling { position: absolute; top: -50px; z-index: 2; pointer-events: none; animation: fall 5s linear forwards; }

        /* Buttons */
        .btn-traditional { 
            padding: 15px 40px; font-size: 22px; background: var(--maroon); color: var(--gold); 
            border: 3px solid var(--gold); border-radius: 10px; cursor: pointer; font-weight: bold;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3); transition: 0.3s;
        }
        .btn-traditional:hover { transform: scale(1.05); background: #a00000; }

        /* Om Revolving with Aura */
        .om-wrap { position: relative; padding: 50px; }
        .om-revolving { font-size: 150px; display: inline-block; animation: rotate 10s linear infinite; color: var(--maroon); filter: drop-shadow(0 0 15px #FFD700); cursor: pointer; }
        .blessing-msg { font-size: 32px; color: #b35900; margin-top: 20px; opacity: 0; transform: scale(0.5); transition: 1s all cubic-bezier(0.175, 0.885, 0.32, 1.275); }

        /* Animations */
        @keyframes flyPath {
            0% { left: -10%; top: 20%; transform: scaleX(1); }
            49% { left: 110%; top: 10%; transform: scaleX(1); }
            50% { left: 110%; top: 10%; transform: scaleX(-1); }
            100% { left: -10%; top: 20%; transform: scaleX(-1); }
        }
        @keyframes fall { to { transform: translateY(110vh) rotate(720deg); } }
        @keyframes glow { from { filter: drop-shadow(0 0 10px #FF9933); } to { filter: drop-shadow(0 0 30px #FFD700); } }
        @keyframes rotate { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        @keyframes ring { from { transform: rotate(-15deg); } to { transform: rotate(15deg); } }
    </style>
</head>
<body>

    <div class="toran">🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃🌿🍃</div>

    <div id="page1" class="page">
        <h1 style="color: var(--maroon); font-size: 40px; margin-bottom: 0;">🙏 నమస్కారం</h1>
        <h2 style="color: #d35400; font-size: 28px;">విశ్వావసు నామ సంవత్సర శుభాకాంక్షలు</h2>
        
        <div class="bird-fly">🕊️</div>
        
        <div class="temple-container">
            <div class="temple">🛕</div>
            <div style="font-size: 60px; margin-top: -30px;">🥥</div>
        </div>

        <div class="bell-box" onclick="playBell()">
            <div id="bell" class="bell-btn">🔔</div>
            <p style="color: var(--maroon); font-weight: bold;">Tap to Ring Bell</p>
        </div>

        <button class="btn-traditional" onclick="nextPage()">Click for Blessings ✨</button>
    </div>

    <div id="page2" class="page">
        <div class="om-wrap" onclick="showBlessings()">
            <div class="om-revolving">🕉️</div>
            <p style="color: var(--maroon);">Tap the Holy Om</p>
        </div>
        
        <div id="blessingMsg" class="blessing-msg">
            ✨ శ్రీరామరక్ష సర్వజగద్రక్ష ✨<br>
            <span style="font-size: 24px;">దేవుని ఆశీస్సులు మీకు ఎల్లప్పుడూ ఉండాలి!</span>
        </div>

        <button class="btn-traditional" onclick="prevPage()" style="margin-top: 40px; font-size: 16px;">⬅ Back to Start</button>
    </div>

    <script>
        // Enhanced Falling Items (Mangoes and Leaves)
        function createFallingItem() {
            const items = ['🍃', '🌿', '🥭', '🌸'];
            const item = document.createElement('div');
            item.classList.add('falling');
            item.innerText = items[Math.floor(Math.random() * items.length)];
            item.style.left = Math.random() * 100 + 'vw';
            item.style.fontSize = Math.random() * 20 + 25 + 'px';
            item.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(item);
            setTimeout(() => item.remove(), 5000);
        }
        setInterval(createFallingItem, 300);

        // Professional Bell Sound & Animation
        function playBell() {
            const bell = document.getElementById('bell');
            bell.classList.add('bell-ring');
            
            // Audio context for a rich "Ding"
            const context = new (window.AudioContext || window.webkitAudioContext)();
            const osc = context.createOscillator();
            const gain = context.createGain();
            osc.connect(gain);
            gain.connect(context.destination);
            osc.type = 'sine';
            osc.frequency.setValueAtTime(880, context.currentTime);
            osc.frequency.exponentialRampToValueAtTime(440, context.currentTime + 0.5);
            gain.gain.setValueAtTime(0.5, context.currentTime);
            gain.gain.exponentialRampToValueAtTime(0.01, context.currentTime + 1);
            osc.start();
            osc.stop(context.currentTime + 1);

            setTimeout(() => bell.classList.remove('bell-ring'), 1000);
        }

        // Navigation (Vertical Slide)
        function nextPage() {
            document.getElementById('page1').style.transform = 'translateY(-100%)';
            document.getElementById('page2').style.transform = 'translateY(0)';
        }
        function prevPage() {
            document.getElementById('page1').style.transform = 'translateY(0)';
            document.getElementById('page2').style.transform = 'translateY(100%)';
        }

        // Blessing Reveal Animation
        function showBlessings() {
            const msg = document.getElementById('blessingMsg');
            msg.style.opacity = '1';
            msg.style.transform = 'scale(1)';
        }
    </script>
</body>
</html>
