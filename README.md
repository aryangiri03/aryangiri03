<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aryan Giri - Cyberpunk Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: #0a0e27;
            color: #00ff41;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Background */
        .cyber-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: 
                linear-gradient(45deg, #0a0e27 25%, transparent 25%),
                linear-gradient(-45deg, #0a0e27 25%, transparent 25%),
                linear-gradient(45deg, transparent 75%, #0f1729 75%),
                linear-gradient(-45deg, transparent 75%, #0f1729 75%);
            background-size: 50px 50px;
            background-position: 0 0, 0 25px, 25px -25px, -25px 0px;
            animation: moveGrid 20s linear infinite;
        }

        /* Floating Particles */
        .particle {
            position: fixed;
            width: 3px;
            height: 3px;
            background: #00ff41;
            border-radius: 50%;
            box-shadow: 0 0 10px #00ff41;
            animation: float 10s infinite;
            z-index: -1;
        }

        /* Glitch Effect Lines */
        .glitch-line {
            position: fixed;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, #ff00de, transparent);
            animation: glitchMove 3s infinite;
            z-index: -1;
            opacity: 0.3;
        }

        /* Container */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 40px 20px;
            position: relative;
        }

        /* Header Section */
        .header {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .logo-container {
            display: inline-block;
            position: relative;
            margin-bottom: 30px;
        }

        .logo {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            border: 4px solid #00ff41;
            box-shadow: 
                0 0 20px #00ff41,
                0 0 40px #00ff41,
                inset 0 0 20px rgba(0, 255, 65, 0.2);
            animation: pulse 2s infinite, rotate 10s linear infinite;
        }

        .hologram {
            position: absolute;
            top: -20px;
            left: -20px;
            right: -20px;
            bottom: -20px;
            border: 2px solid #ff00de;
            border-radius: 50%;
            opacity: 0.3;
            animation: hologramPulse 3s infinite;
        }

        .title {
            font-size: 4em;
            font-weight: bold;
            background: linear-gradient(45deg, #00ff41, #00d4ff, #ff00de);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: textGlow 2s infinite alternate;
            text-shadow: 0 0 30px rgba(0, 255, 65, 0.5);
            margin: 20px 0;
            letter-spacing: 5px;
        }

        .subtitle {
            font-size: 1.5em;
            color: #00d4ff;
            text-shadow: 0 0 10px #00d4ff;
            margin: 15px 0;
            animation: flicker 3s infinite;
        }

        .typing-text {
            font-size: 1.2em;
            color: #ff00de;
            height: 30px;
            overflow: hidden;
            border-right: 3px solid #ff00de;
            animation: blink 0.7s infinite;
            display: inline-block;
            padding-right: 5px;
        }

        /* Stats Badge */
        .stats-badge {
            display: inline-block;
            margin: 20px 0;
            animation: float 3s ease-in-out infinite;
        }

        /* About Section */
        .about-section {
            background: rgba(15, 23, 42, 0.8);
            border: 2px solid #00ff41;
            border-radius: 20px;
            padding: 40px;
            margin: 40px 0;
            position: relative;
            box-shadow: 
                0 0 30px rgba(0, 255, 65, 0.3),
                inset 0 0 30px rgba(0, 255, 65, 0.1);
            animation: borderGlow 3s infinite;
            backdrop-filter: blur(10px);
        }

        .about-section::before {
            content: '< SYSTEM_INFO />';
            position: absolute;
            top: -15px;
            left: 30px;
            background: #0a0e27;
            padding: 5px 15px;
            color: #00ff41;
            font-size: 0.9em;
            border: 1px solid #00ff41;
        }

        .code-block {
            background: #000;
            border: 1px solid #00ff41;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
            position: relative;
            overflow: hidden;
        }

        .code-block::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 65, 0.1), transparent);
            animation: scan 3s infinite;
        }

        .code-line {
            margin: 8px 0;
            animation: fadeIn 0.5s;
        }

        .keyword { color: #ff00de; }
        .string { color: #00d4ff; }
        .function { color: #00ff41; }
        .comment { color: #666; opacity: 0.7; }

        /* Skills Grid */
        .skills-section {
            margin: 60px 0;
        }

        .section-title {
            font-size: 2.5em;
            text-align: center;
            margin: 40px 0;
            color: #00ff41;
            text-shadow: 0 0 20px #00ff41;
            position: relative;
            display: inline-block;
            width: 100%;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 200px;
            height: 2px;
            background: linear-gradient(90deg, transparent, #00ff41, transparent);
            animation: lineExpand 2s infinite;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }

        .skill-card {
            background: rgba(0, 0, 0, 0.6);
            border: 2px solid #00ff41;
            border-radius: 15px;
            padding: 25px;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            animation: float 4s ease-in-out infinite;
        }

        .skill-card:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 
                0 0 40px rgba(0, 255, 65, 0.6),
                inset 0 0 20px rgba(0, 255, 65, 0.2);
            border-color: #ff00de;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 65, 0.1), transparent);
            animation: rotate 4s linear infinite;
        }

        .skill-icon {
            font-size: 3em;
            margin-bottom: 15px;
            display: inline-block;
            animation: bounce 2s infinite;
        }

        .skill-name {
            font-size: 1.4em;
            color: #00d4ff;
            margin-bottom: 15px;
            text-shadow: 0 0 10px #00d4ff;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: rgba(0, 255, 65, 0.2);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #00ff41, #00d4ff);
            border-radius: 10px;
            box-shadow: 0 0 15px #00ff41;
            animation: fillProgress 2s ease-out;
            position: relative;
        }

        .progress-fill::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            animation: shimmer 2s infinite;
        }

        .percentage {
            text-align: right;
            margin-top: 8px;
            color: #00ff41;
            font-size: 0.9em;
        }

        /* Tools Section */
        .tools-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin: 40px 0;
        }

        .tool-badge {
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #ff00de;
            border-radius: 15px;
            padding: 20px 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            transition: all 0.3s;
            animation: float 3s ease-in-out infinite;
            position: relative;
            overflow: hidden;
        }

        .tool-badge:hover {
            transform: scale(1.15) rotate(5deg);
            box-shadow: 0 0 30px rgba(255, 0, 222, 0.8);
            border-color: #00ff41;
        }

        .tool-badge::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255, 0, 222, 0.1), transparent);
            animation: rotate 3s linear infinite;
        }

        .tool-icon {
            font-size: 2.5em;
            filter: drop-shadow(0 0 10px currentColor);
        }

        .tool-name {
            color: #00d4ff;
            font-size: 0.9em;
            text-shadow: 0 0 5px #00d4ff;
        }

        /* Quick Facts */
        .facts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }

        .fact-card {
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #00d4ff;
            border-radius: 20px;
            padding: 30px;
            position: relative;
            overflow: hidden;
            animation: float 5s ease-in-out infinite;
        }

        .fact-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 212, 255, 0.2), transparent);
            animation: scan 4s infinite;
        }

        .fact-icon {
            font-size: 2.5em;
            margin-bottom: 15px;
            display: inline-block;
            animation: pulse 2s infinite;
        }

        .fact-title {
            font-size: 1.3em;
            color: #00ff41;
            margin-bottom: 10px;
            text-shadow: 0 0 10px #00ff41;
        }

        .fact-text {
            color: #00d4ff;
            line-height: 1.6;
        }

        /* Connect Section */
        .connect-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin: 40px 0;
        }

        .connect-btn {
            background: rgba(0, 0, 0, 0.8);
            border: 2px solid #00ff41;
            border-radius: 12px;
            padding: 15px 30px;
            color: #00ff41;
            text-decoration: none;
            font-size: 1.1em;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .connect-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(0, 255, 65, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.5s, height 0.5s;
        }

        .connect-btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .connect-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 30px rgba(0, 255, 65, 0.8);
            border-color: #ff00de;
            color: #ff00de;
        }

        .connect-icon {
            font-size: 1.5em;
            z-index: 1;
        }

        .connect-text {
            z-index: 1;
        }

        /* GitHub Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }

        .stat-container {
            background: rgba(0, 0, 0, 0.6);
            border: 2px solid #00ff41;
            border-radius: 15px;
            padding: 15px;
            overflow: hidden;
            position: relative;
            animation: borderGlow 3s infinite;
        }

        .stat-container:hover {
            transform: scale(1.05);
            box-shadow: 0 0 40px rgba(0, 255, 65, 0.6);
        }

        .stat-container img {
            width: 100%;
            border-radius: 10px;
        }

        /* Footer */
        .footer {
            text-align: center;
            margin: 60px 0 40px;
            padding: 30px;
            border-top: 2px solid #00ff41;
            position: relative;
        }

        .footer-text {
            font-size: 1.2em;
            color: #00d4ff;
            font-style: italic;
            text-shadow: 0 0 10px #00d4ff;
            margin: 20px 0;
            animation: flicker 4s infinite;
        }

        /* Animations */
        @keyframes moveGrid {
            0% { background-position: 0 0, 0 25px, 25px -25px, -25px 0px; }
            100% { background-position: 50px 50px, 50px 75px, 75px 25px, 25px 50px; }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) translateX(0px); }
            25% { transform: translateY(-20px) translateX(10px); }
            50% { transform: translateY(-10px) translateX(-10px); }
            75% { transform: translateY(-15px) translateX(5px); }
        }

        @keyframes glitchMove {
            0% { top: 10%; opacity: 0.3; }
            50% { top: 50%; opacity: 0.5; }
            100% { top: 90%; opacity: 0.3; }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes hologramPulse {
            0%, 100% { transform: scale(1); opacity: 0.3; }
            50% { transform: scale(1.1); opacity: 0.6; }
        }

        @keyframes textGlow {
            0% { text-shadow: 0 0 20px rgba(0, 255, 65, 0.5); }
            100% { text-shadow: 0 0 40px rgba(0, 255, 65, 0.8), 0 0 60px rgba(255, 0, 222, 0.5); }
        }

        @keyframes flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }

        @keyframes blink {
            0%, 100% { border-color: #ff00de; }
            50% { border-color: transparent; }
        }

        @keyframes borderGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(0, 255, 65, 0.3); }
            50% { box-shadow: 0 0 40px rgba(0, 255, 65, 0.6), 0 0 60px rgba(255, 0, 222, 0.3); }
        }

        @keyframes scan {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateX(-10px); }
            to { opacity: 1; transform: translateX(0); }
        }

        @keyframes lineExpand {
            0%, 100% { width: 200px; }
            50% { width: 300px; }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        @keyframes fillProgress {
            from { width: 0; }
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .title { font-size: 2.5em; }
            .subtitle { font-size: 1.2em; }
            .skills-grid, .stats-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="cyber-bg"></div>
    
    <!-- Glitch Lines -->
    <div class="glitch-line" style="top: 20%;"></div>
    <div class="glitch-line" style="top: 60%; animation-delay: 1s;"></div>
    <div class="glitch-line" style="top: 85%; animation-delay: 2s;"></div>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo-container">
                <div class="hologram"></div>
                <img src="https://user-images.githubusercontent.com/90236635/232446433-d5540fa2-fe28-4bb8-b929-cdb51fe61336.gif" alt="Logo" class="logo">
            </div>
            <h1 class="title">ARYAN GIRI</h1>
            <p class="subtitle">⚡ FULL STACK DEVELOPER | DATA SCIENTIST | ML ENGINEER ⚡</p>
            <div class="typing-text" id="typingText"></div>
            <div class="stats-badge">
                <img src="https://komarev.com/ghpvc/?username=aryangiri03&label=SYSTEM%20ACCESS&color=00ff41&style=for-the-badge" alt="Profile Views">
            </div>
        </div>

        <!-- About Section -->
        <div class="about-section">
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px; align-items: center;">
                <div class="code-block">
                    <div class="code-line"><span class="keyword">class</span> <span class="function">AryanGiri</span>:</div>
                    <div class="code-line">    <span class="keyword">def</span> <span class="function">__init__</span>(self):</div>
                    <div class="code-line">        self.role = <span class="string">"Computer Engineer"</span></div>
                    <div class="code-line">        self.year = <span class="string">"Final Year"</span></div>
                    <div class="code-line">        self.passions = [<span class="string">"AI"</span>, <span class="string">"ML"</span>, <span class="string">"Web"</span>]</div>
                    <div class="code-line">        self.learning = <span class="string">"Data Science"</span></div>
                    <div class="code-line">    </div>
                    <div class="code-line">    <span class="keyword">def</span> <span class="function">get_skills</span>(self):</div>
                    <div class="code-line">        <span class="keyword">return</span> {</div>
                    <div class="code-line">            <span class="string">"languages"</span>: [<span class="string">"Python"</span>, <span class="string">"C"</span>, <span class="string">"C++"</span>],</div>
                    <div class="code-line">            <span class="string">"web"</span>: [<span class="string">"HTML"</span>, <span class="string">"CSS"</span>, <span class="string">"JS"</span>],</div>
                    <div class="code-line">            <span class="string">"data"</span>: [<span class="string">"ML"</span>, <span class="string">"SQL"</span>, <span class="string">"Analytics"</span>]</div>
                    <div class="code-line">        }</div>
                    <div class="code-line">    </div>
                    <div class="code-line"><span class="comment"># Initialize system</span></div>
                    <div class="code-line">dev = AryanGiri()</div>
                    <div class="code-line">print(<span class="string">"Ready to innovate! 🚀"</span>)</div>
                </div>
                <div>
                    <img src="https://media0.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif?cid=ecf05e47y55lbzk2r7co88iy6b21ywwekg9ip4hy1uudpsu1&ep=v1_gifs_search&rid=giphy.gif&ct=g" alt="Coding" style="width: 100%; border-radius: 20px; border: 2px solid #00ff41; box-shadow: 0 0 30px rgba(0, 255, 65, 0.5);">
                </div>
            </div>
        </div>

        <!-- Quick Facts -->
        <h2 class="section-title">&lt; CURRENT_STATUS /&gt;</h2>
        <div class="facts-grid">
            <div class="fact-card" style="animation-delay: 0s;">
                <div class="fact-icon">🌱</div>
                <div class="fact-title">LEARNING</div>
                <div class="fact-text">Advanced Data Science & Machine Learning algorithms</div>
            </div>
            <div class="fact-card" style="animation-delay: 0.5s;">
                <div class="fact-icon">💬</div>
                <div class="fact-title">ASK ME ABOUT</div>
                <div class="fact-text">Python, C Programming, Web Tech, SQL, Machine Learning</div>
            </div>
            <div class="fact-card" style="animation-delay: 1s;">
                <div class="fact-icon">📫</div>
                <div class="fact-title">REACH ME</div>
                <div class="fact-text">aaryanmgiri@gmail.com</div>
            </div>
        </div>

        <!-- Skills Section -->
        <h2 class="section-title">&lt; TECH_ARSENAL /&gt;</h2>
        <div class="skills-grid">
            <div class="skill-card" style="animation-delay: 0s;">
                <div class="skill-icon">🐍</div>
                <div class="skill-name">Python</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 95%;"></div>
                </div>
                <div class="percentage">95%</div>
            </div>
            <div class="skill-card" style="animation-delay: 0.2s;">
                <div class="skill-icon">⚡</div>
                <div class="skill-name">C / C++</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 90%;"></div>
                </div>
                <div class="percentage">90%</div>
            </div>
            <div class="skill-card" style="animation-delay: 0.4s;">
                <div class="skill-icon">💛</div>
                <div class="skill-name">JavaScript</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 85%;"></div>
                </div>
                <div class="percentage">85%</div>
            </div>
            <div class="skill-card" style="animation-delay: 0.6s;">
                <div class="skill-icon">📊</div>
                <div class="skill-name">Data Science</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 88%;"></div>
                </div>
                <div class="percentage">88%</div>
            </div>
            <div class="skill-card" style="animation-delay: 0.8s;">
                <div class="skill-icon">🤖</div>
                <div class="skill-name">Machine Learning</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 82%;"></div>
                </div>
                <div class="percentage">82%</div>
            </div>
            <div class="skill-card" style="animation-delay: 1s;">
                <div class="skill-icon">🌐</div>
                <div class="skill-name">Web Development</div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 87%;"></div>
                </div>
                <div class="percentage">87%</div>
            </div>
        </div>

        <!-- Tools Section -->
        <h2 class="section-title">&lt; TOOLS_AND_TECH /&gt;</h2>
        <div class="tools-grid">
            <div class="tool-badge" style="animation-delay: 0s;">
                <div class="tool-icon">☁️</div>
                <div class="tool-name">AWS</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.1s;">
                <div class="tool-icon">📦</div>
                <div class="tool-name">Git</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.2s;">
                <div class="tool-icon">📱</div>
                <div class="tool-name">Flutter</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.3s;">
                <div class="tool-icon">🎨</div>
                <div class="tool-name">Tailwind</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.4s;">
                <div class="tool-icon">🗃️</div>
                <div class="tool-name">SQL</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.5s;">
                <div class="tool-icon">🎭</div>
                <div class="tool-name">Figma</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.6s;">
                <div class="tool-icon">🔧</div>
                <div class="tool-name">Postman</div>
            </div>
            <div class="tool-badge" style="animation-delay: 0.7s;">
                <div class="tool-icon">📐</div>
                <div class="tool-name">MATLAB</div>
            </div>
        </div>

        <!-- Connect Section -->
        <h2 class="section-title">&lt; CONNECT_NETWORK /&gt;</h2>
        <div class="connect-grid">
            <a href="https://in.linkedin.com/in/aryan-giri-852a0a259" target="_blank" class="connect-btn">
                <span class="connect-icon">💼</span>
                <span class="connect-text">LinkedIn</span>
            </a>
            <a href="https://github.com/aryangiri03" target="_blank" class="connect-btn">
                <span class="connect-icon">🐙</span>
                <span class="connect-text">GitHub</span>
            </a>
            <a href="mailto:aaryanmgiri@gmail.com" class="connect-btn">
                <span class="connect-icon">📧</span>
                <span class="connect-text">Email</span>
            </a>
            <a href="https://stackoverflow.com/users/23186353/aryan-giri" target="_blank" class="connect-btn">
                <span class="connect-icon">⭐</span>
                <span class="connect-text">StackOverflow</span>
            </a>
            <a href="https://auth.geeksforgeeks.org/user/aryangiri03" target="_blank" class="connect-btn">
                <span class="connect-icon">💚</span>
                <span class="connect-text">GeeksforGeeks</span>
            </a>
            <a href="https://replit.com/@engineeringstu3" target="_blank" class="connect-btn">
                <span class="connect-icon">🔄</span>
                <span class="connect-text">Replit</span>
            </a>
        </div>

        <!-- GitHub Stats -->
        <h2 class="section-title">&lt; GITHUB_ANALYTICS /&gt;</h2>
        <div class="stats-grid">
            <div class="stat-container">
                <img src="https://github-readme-stats.vercel.app/api?username=aryangiri03&show_icons=true&theme=radical&hide_border=true&bg_color=0d1117&title_color=00ff41&icon_color=00d4ff&text_color=00ff41" alt="GitHub Stats">
            </div>
            <div class="stat-container">
                <img src="https://github-readme-streak-stats.herokuapp.com/?user=aryangiri03&theme=radical&hide_border=true&background=0d1117&ring=00ff41&fire=ff00de&currStreakLabel=00d4ff" alt="GitHub Streak">
            </div>
        </div>
        
        <div class="stat-container" style="max-width: 800px; margin: 25px auto;">
            <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aryangiri03&layout=compact&theme=radical&hide_border=true&bg_color=0d1117&title_color=00ff41&text_color=00d4ff" alt="Top Languages">
        </div>

        <!-- Footer -->
        <div class="footer">
            <p class="footer-text">
                "By day, I'm a code maestro weaving Python and C spells;<br>
                by night, a tech geek sculpting digital wonders and unleashing magic in the tech cosmos! 🌟"
            </p>
            <div style="margin-top: 30px; font-size: 1.1em; color: #00ff41;">
                ✨ &lt; THANKS_FOR_VISITING /&gt; ✨
            </div>
            <div style="margin-top: 20px; color: #666; font-size: 0.9em;">
                [ SYSTEM ONLINE | ALL MODULES OPERATIONAL ]
            </div>
        </div>
    </div>

    <script>
        // Typing Effect
        const texts = [
            "Code maestro by day 🌞",
            "Tech geek by night 🌙",
            "Data Science enthusiast 📊",
            "Building the future 🚀"
        ];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingSpeed = 100;
        const deletingSpeed = 50;
        const pauseTime = 2000;

        function typeText() {
            const currentText = texts[textIndex];
            const typingElement = document.getElementById('typingText');

            if (!isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;

                if (charIndex === currentText.length) {
                    isDeleting = true;
                    setTimeout(typeText, pauseTime);
                    return;
                }
            } else {
                typingElement.textContent = currentText.substring(0, charIndex);
                charIndex--;

                if (charIndex === 0) {
                    isDeleting = false;
                    textIndex = (textIndex + 1) % texts.length;
                }
            }

            setTimeout(typeText, isDeleting ? deletingSpeed : typingSpeed);
        }

        // Generate Floating Particles
        function createParticles() {
            const particleCount = 30;
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDuration = (5 + Math.random() * 10) + 's';
                particle.style.animationDelay = Math.random() * 5 + 's';
                document.body.appendChild(particle);
            }
        }

        // Skill Cards Stagger Animation
        function animateSkillCards() {
            const skillCards = document.querySelectorAll('.skill-card');
            skillCards.forEach((card, index) => {
                card.style.animationDelay = (index * 0.15) + 's';
            });
        }

        // Tool Badges Stagger Animation
        function animateToolBadges() {
            const toolBadges = document.querySelectorAll('.tool-badge');
            toolBadges.forEach((badge, index) => {
                badge.style.animationDelay = (index * 0.1) + 's';
            });
        }

        // Initialize
        window.addEventListener('DOMContentLoaded', () => {
            createParticles();
            typeText();
            animateSkillCards();
            animateToolBadges();
        });

        // Mouse Trail Effect
        document.addEventListener('mousemove', (e) => {
            const trail = document.createElement('div');
            trail.className = 'particle';
            trail.style.left = e.pageX + 'px';
            trail.style.top = e.pageY + 'px';
            trail.style.position = 'absolute';
            trail.style.pointerEvents = 'none';
            document.body.appendChild(trail);

            setTimeout(() => {
                trail.remove();
            }, 1000);
        });
    </script>
</body>
</html>
