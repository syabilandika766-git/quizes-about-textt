<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔤 DEMOX TEXT QUIZ - TEBAK TEKS DALAM FONT 🔤</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 30px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 60px;
            padding: 40px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3);
        }

        /* HEADER */
        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .logo {
            font-size: 70px;
            margin-bottom: 10px;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%,100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        h1 {
            font-size: 42px;
            color: #333;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 18px;
            color: #666;
        }

        /* DIFFICULTY SELECTOR */
        .difficulty-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .difficulty-btn {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            color: white;
        }

        .difficulty-btn.easy {
            background: linear-gradient(135deg, #00b09b, #96c93d);
        }
        .difficulty-btn.medium {
            background: linear-gradient(135deg, #f7971e, #ffd200);
        }
        .difficulty-btn.hard {
            background: linear-gradient(135deg, #ff416c, #ff4b2b);
        }
        .difficulty-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }
        .difficulty-btn.active {
            transform: scale(1.05);
            box-shadow: 0 0 0 3px white, 0 10px 20px rgba(0,0,0,0.3);
        }

        /* STATS BAR */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 25px;
        }

        .stat-card {
            background: white;
            border-radius: 25px;
            padding: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .stat-value {
            font-size: 32px;
            font-weight: bold;
            color: #667eea;
        }
        .stat-label {
            color: #666;
            font-size: 13px;
            margin-top: 5px;
        }

        /* PROGRESS */
        .progress-container {
            margin-bottom: 25px;
        }
        .progress-bar {
            width: 100%;
            height: 15px;
            background: #f0f0f0;
            border-radius: 30px;
            overflow: hidden;
        }
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            width: 0%;
            transition: width 0.3s;
        }
        .progress-text {
            text-align: right;
            color: #666;
            margin-top: 5px;
            font-size: 13px;
        }

        /* GAME AREA */
        .game-area {
            background: #f8f9fa;
            border-radius: 40px;
            padding: 30px;
            margin-bottom: 30px;
        }

        .question-box {
            text-align: center;
            margin-bottom: 30px;
        }

        .question-label {
            font-size: 16px;
            color: #666;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .font-display {
            background: white;
            border-radius: 30px;
            padding: 40px 20px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            border: 3px solid #f0f0f0;
            word-wrap: break-word;
        }

        #questionText {
            font-size: 48px;
            line-height: 1.4;
            transition: all 0.3s;
        }

        .hint-box {
            background: #e8f4fd;
            border-radius: 20px;
            padding: 15px;
            margin: 15px 0;
            font-size: 16px;
            color: #0369a1;
            border-left: 5px solid #0ea5e9;
        }

        /* INPUT AREA */
        .input-area {
            margin: 30px 0;
        }

        .answer-input {
            width: 100%;
            padding: 20px 25px;
            border: 3px solid #e0e0e0;
            border-radius: 60px;
            font-size: 20px;
            outline: none;
            transition: 0.3s;
            margin-bottom: 15px;
        }

        .answer-input:focus {
            border-color: #667eea;
            box-shadow: 0 0 0 4px rgba(102,126,234,0.1);
        }

        .answer-input.correct {
            border-color: #00b09b;
            background: #f0fff4;
        }

        .answer-input.wrong {
            border-color: #ff416c;
            background: #fff0f0;
        }

        .button-group {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            flex: 1;
            min-width: 150px;
        }

        .btn-secondary {
            background: white;
            border: 2px solid #e0e0e0;
            color: #333;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        .btn:disabled {
            opacity: 0.5;
            pointer-events: none;
        }

        /* FEEDBACK */
        .feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 30px;
            text-align: center;
            font-size: 18px;
            font-weight: 600;
            display: none;
        }

        .feedback.correct {
            background: #d4edda;
            color: #155724;
            display: block;
        }

        .feedback.wrong {
            background: #f8d7da;
            color: #721c24;
            display: block;
        }

        /* TABLE OF CONTENTS */
        .table-section {
            background: white;
            border-radius: 40px;
            padding: 25px;
            margin-top: 30px;
        }

        .table-title {
            font-size: 22px;
            color: #333;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .difficulty-tag {
            padding: 5px 15px;
            border-radius: 30px;
            font-size: 14px;
            font-weight: 600;
            color: white;
        }
        .tag-easy { background: #00b09b; }
        .tag-medium { background: #f7971e; }
        .tag-hard { background: #ff416c; }

        .question-list {
            max-height: 400px;
            overflow-y: auto;
            padding-right: 10px;
        }

        .question-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 12px;
            border-bottom: 1px solid #f0f0f0;
            cursor: pointer;
            transition: 0.2s;
        }

        .question-item:hover {
            background: #f8f9fa;
            transform: translateX(5px);
        }

        .question-item.current {
            background: #e8f0fe;
            border-left: 4px solid #667eea;
        }

        .q-num {
            width: 35px;
            height: 35px;
            background: #f0f0f0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #666;
        }

        .q-preview {
            flex: 1;
            font-size: 14px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .q-status {
            width: 20px;
            height: 20px;
            border-radius: 50%;
        }
        .status-correct { background: #00b09b; }
        .status-wrong { background: #ff416c; }
        .status-pending { background: #e0e0e0; }

        /* MODAL */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            pointer-events: none;
            transition: 0.3s;
        }

        .modal-overlay.show {
            opacity: 1;
            pointer-events: all;
        }

        .modal {
            background: white;
            border-radius: 50px;
            padding: 50px;
            max-width: 450px;
            text-align: center;
            transform: scale(0);
            transition: 0.3s;
        }

        .modal-overlay.show .modal {
            transform: scale(1);
        }

        .modal-icon {
            font-size: 80px;
            margin-bottom: 20px;
        }

        .modal-title {
            font-size: 32px;
            color: #333;
            margin-bottom: 15px;
        }

        .modal-stats {
            background: #f8f9fa;
            border-radius: 30px;
            padding: 25px;
            margin: 25px 0;
        }

        .modal-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
        }

        /* FOOTER */
        .footer {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 2px solid #f0f0f0;
            color: #999;
        }

        .emoji-wall {
            font-size: 25px;
            margin: 15px 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- HEADER -->
        <div class="header">
            <div class="logo">🔤</div>
            <h1>DEMOX TEXT QUIZ</h1>
            <div class="subtitle">Tebak TEKS-nya, bukan fontnya! • 100 Pertanyaan</div>
        </div>

        <!-- DIFFICULTY -->
        <div class="difficulty-container">
            <button class="difficulty-btn easy active" onclick="setDifficulty('easy')">✨ EASY (30)</button>
            <button class="difficulty-btn medium" onclick="setDifficulty('medium')">⚡ MEDIUM (35)</button>
            <button class="difficulty-btn hard" onclick="setDifficulty('hard')">🔥 HARD (35)</button>
        </div>

        <!-- STATS -->
        <div class="stats-bar">
            <div class="stat-card">
                <div class="stat-value" id="scoreDisplay">0</div>
                <div class="stat-label">SCORE</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="totalDisplay">0/30</div>
                <div class="stat-label">PROGRESS</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="streakDisplay">0</div>
                <div class="stat-label">STREAK</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="accuracyDisplay">0%</div>
                <div class="stat-label">ACCURACY</div>
            </div>
        </div>

        <!-- PROGRESS BAR -->
        <div class="progress-container">
            <div class="progress-bar">
                <div class="progress-fill" id="progressFill" style="width: 0%"></div>
            </div>
            <div class="progress-text" id="progressText">0/30 questions</div>
        </div>

        <!-- GAME AREA -->
        <div class="game-area">
            <div class="question-box">
                <div class="question-label">🔍 TEKS APA INI?</div>
                <div class="font-display">
                    <div id="questionText">BroDemox</div>
                </div>
                <div class="hint-box" id="hintBox">
                    💡 Hint: Ketik teks yang kamu lihat persis seperti ini
                </div>
            </div>

            <!-- INPUT ANSWER -->
            <div class="input-area">
                <input type="text" class="answer-input" id="answerInput" placeholder="Ketik jawaban di sini..." autocomplete="off">
                
                <div class="button-group">
                    <button class="btn btn-primary" onclick="checkAnswer()">✅ CEK JAWABAN</button>
                    <button class="btn btn-secondary" onclick="nextQuestion()">⏭️ NEXT</button>
                    <button class="btn btn-secondary" onclick="skipQuestion()">⏩ SKIP</button>
                </div>

                <div class="feedback" id="feedback"></div>
            </div>
        </div>

        <!-- TABLE OF QUESTIONS -->
        <div class="table-section">
            <div class="table-title">
                <span>📋 DAFTAR PERTANYAAN</span>
                <span class="difficulty-tag tag-easy" id="currentDifficultyTag">EASY</span>
            </div>
            <div class="question-list" id="questionList"></div>
        </div>

        <!-- FOOTER -->
        <div class="footer">
            <div class="emoji-wall">
                🥶🤬😡😠😤👿😈👹👺🤖☠️💀👻👽👾🖕
            </div>
            <p>🔥 DEMOX TEXT QUIZ - 100 Pertanyaan dengan berbagai font! 🔥</p>
        </div>
    </div>

    <!-- MODAL RESULT -->
    <div class="modal-overlay" id="resultModal">
        <div class="modal">
            <div class="modal-icon">🏆</div>
            <div class="modal-title" id="modalTitle">QUIZ COMPLETE!</div>
            <div class="modal-stats" id="modalStats"></div>
            <button class="modal-btn" onclick="closeModal()">PLAY AGAIN</button>
        </div>
    </div>

    <script>
        // ==================== 100 PERTANYAAN ====================
        const questions = [
            // EASY - 30 pertanyaan (teks pendek, 1-3 kata)
            { text: 'BroDemox', font: 'Arial, sans-serif', difficulty: 'easy' },
            { text: 'Hello World', font: 'Times New Roman, serif', difficulty: 'easy' },
            { text: 'DEMOX', font: 'Courier New, monospace', difficulty: 'easy' },
            { text: '12345', font: 'Georgia, serif', difficulty: 'easy' },
            { text: 'Game Quiz', font: 'Verdana, sans-serif', difficulty: 'easy' },
            { text: 'Font Test', font: 'Comic Sans MS, cursive', difficulty: 'easy' },
            { text: 'BOLD TEXT', font: 'Impact, sans-serif', difficulty: 'easy' },
            { text: 'Universe', font: 'Trebuchet MS, sans-serif', difficulty: 'easy' },
            { text: 'Planet', font: 'Palatino, serif', difficulty: 'easy' },
            { text: 'Stars', font: 'Garamond, serif', difficulty: 'easy' },
            { text: 'Coffee', font: 'Helvetica, sans-serif', difficulty: 'easy' },
            { text: 'Pizza', font: 'Futura, sans-serif', difficulty: 'easy' },
            { text: 'Music', font: 'Baskerville, serif', difficulty: 'easy' },
            { text: 'Dance', font: 'Gill Sans, sans-serif', difficulty: 'easy' },
            { text: 'Party', font: 'Rockwell, serif', difficulty: 'easy' },
            { text: 'Happy', font: 'Century Gothic, sans-serif', difficulty: 'easy' },
            { text: 'Smile', font: 'Book Antiqua, serif', difficulty: 'easy' },
            { text: 'Laugh', font: 'Copperplate, fantasy', difficulty: 'easy' },
            { text: 'Code', font: 'Lucida Console, monospace', difficulty: 'easy' },
            { text: 'Script', font: 'Brush Script MT, cursive', difficulty: 'easy' },
            { text: 'Alpha', font: 'Arial Black, sans-serif', difficulty: 'easy' },
            { text: 'Beta', font: 'Calibri, sans-serif', difficulty: 'easy' },
            { text: 'Gamma', font: 'Cambria, serif', difficulty: 'easy' },
            { text: 'Delta', font: 'Candara, sans-serif', difficulty: 'easy' },
            { text: 'Epsilon', font: 'Consolas, monospace', difficulty: 'easy' },
            { text: 'Zeta', font: 'Corbel, sans-serif', difficulty: 'easy' },
            { text: 'Eta', font: 'Didot, serif', difficulty: 'easy' },
            { text: 'Theta', font: 'Franklin Gothic, sans-serif', difficulty: 'easy' },
            { text: 'Iota', font: 'Gabriola, cursive', difficulty: 'easy' },
            { text: 'Kappa', font: 'Javanese Text, sans-serif', difficulty: 'easy' },

            // MEDIUM - 35 pertanyaan (teks sedang, 3-6 kata)
            { text: 'The Quick Brown Fox', font: 'Times New Roman, serif', difficulty: 'medium' },
            { text: 'JavaScript is Fun', font: 'Courier New, monospace', difficulty: 'medium' },
            { text: 'Web Development', font: 'Georgia, serif', difficulty: 'medium' },
            { text: 'Artificial Intelligence', font: 'Verdana, sans-serif', difficulty: 'medium' },
            { text: 'Space Exploration', font: 'Comic Sans MS, cursive', difficulty: 'medium' },
            { text: 'Machine Learning', font: 'Impact, sans-serif', difficulty: 'medium' },
            { text: 'Deep Neural Network', font: 'Trebuchet MS, sans-serif', difficulty: 'medium' },
            { text: 'Quantum Computing', font: 'Palatino, serif', difficulty: 'medium' },
            { text: 'Black Hole Theory', font: 'Garamond, serif', difficulty: 'medium' },
            { text: 'Dark Matter Mystery', font: 'Helvetica, sans-serif', difficulty: 'medium' },
            { text: 'Solar System Planets', font: 'Futura, sans-serif', difficulty: 'medium' },
            { text: 'Milky Way Galaxy', font: 'Baskerville, serif', difficulty: 'medium' },
            { text: 'Parallel Universe', font: 'Gill Sans, sans-serif', difficulty: 'medium' },
            { text: 'Time Travel Paradox', font: 'Rockwell, serif', difficulty: 'medium' },
            { text: 'String Theory Physics', font: 'Century Gothic, sans-serif', difficulty: 'medium' },
            { text: 'Particle Accelerator', font: 'Book Antiqua, serif', difficulty: 'medium' },
            { text: 'Nuclear Fusion Reactor', font: 'Copperplate, fantasy', difficulty: 'medium' },
            { text: 'Genetic Engineering', font: 'Lucida Console, monospace', difficulty: 'medium' },
            { text: 'CRISPR Gene Editing', font: 'Brush Script MT, cursive', difficulty: 'medium' },
            { text: 'Biotechnology Advances', font: 'Arial Black, sans-serif', difficulty: 'medium' },
            { text: 'Climate Change Crisis', font: 'Calibri, sans-serif', difficulty: 'medium' },
            { text: 'Renewable Energy Sources', font: 'Cambria, serif', difficulty: 'medium' },
            { text: 'Sustainable Development', font: 'Candara, sans-serif', difficulty: 'medium' },
            { text: 'Electric Vehicle Future', font: 'Consolas, monospace', difficulty: 'medium' },
            { text: 'Autonomous Driving Car', font: 'Corbel, sans-serif', difficulty: 'medium' },
            { text: 'Virtual Reality World', font: 'Didot, serif', difficulty: 'medium' },
            { text: 'Augmented Reality App', font: 'Franklin Gothic, sans-serif', difficulty: 'medium' },
            { text: 'Blockchain Technology', font: 'Gabriola, cursive', difficulty: 'medium' },
            { text: 'Cryptocurrency Bitcoin', font: 'Javanese Text, sans-serif', difficulty: 'medium' },
            { text: 'NFT Digital Art', font: 'Leelawadee, sans-serif', difficulty: 'medium' },
            { text: 'Metaverse Experience', font: 'Malgun Gothic, sans-serif', difficulty: 'medium' },
            { text: 'Web3 Revolution', font: 'Microsoft YaHei, sans-serif', difficulty: 'medium' },
            { text: 'Decentralized Finance', font: 'Segoe UI, sans-serif', difficulty: 'medium' },
            { text: 'Smart Contract Ethereum', font: 'Sylfaen, serif', difficulty: 'medium' },
            { text: 'DAO Governance Model', font: 'Traditional Arabic, serif', difficulty: 'medium' },

            // HARD - 35 pertanyaan (teks panjang, 6-12 kata)
            { text: 'The quick brown fox jumps over the lazy dog', font: 'Times New Roman, serif', difficulty: 'hard' },
            { text: 'JavaScript is a high level programming language', font: 'Courier New, monospace', difficulty: 'hard' },
            { text: 'Full stack web development requires multiple skills', font: 'Georgia, serif', difficulty: 'hard' },
            { text: 'Artificial general intelligence is the holy grail', font: 'Verdana, sans-serif', difficulty: 'hard' },
            { text: 'SpaceX successfully launched starship rocket yesterday', font: 'Comic Sans MS, cursive', difficulty: 'hard' },
            { text: 'Neural networks can recognize complex patterns', font: 'Impact, sans-serif', difficulty: 'hard' },
            { text: 'Quantum entanglement allows instantaneous communication', font: 'Trebuchet MS, sans-serif', difficulty: 'hard' },
            { text: 'Black holes warp spacetime fabric infinitely', font: 'Palatino, serif', difficulty: 'hard' },
            { text: 'Dark energy accelerates universal expansion rate', font: 'Garamond, serif', difficulty: 'hard' },
            { text: 'Milky Way contains billions of exoplanets', font: 'Helvetica, sans-serif', difficulty: 'hard' },
            { text: 'String theory proposes eleven dimensions exist', font: 'Futura, sans-serif', difficulty: 'hard' },
            { text: 'Particle colliders reveal fundamental matter secrets', font: 'Baskerville, serif', difficulty: 'hard' },
            { text: 'Genetic modification could eliminate inherited diseases', font: 'Gill Sans, sans-serif', difficulty: 'hard' },
            { text: 'CRISPR technology revolutionizes gene editing capabilities', font: 'Rockwell, serif', difficulty: 'hard' },
            { text: 'Climate change requires immediate global action', font: 'Century Gothic, sans-serif', difficulty: 'hard' },
            { text: 'Renewable energy sources like solar and wind', font: 'Book Antiqua, serif', difficulty: 'hard' },
            { text: 'Electric vehicles are becoming increasingly affordable', font: 'Copperplate, fantasy', difficulty: 'hard' },
            { text: 'Autonomous driving technology improves safety significantly', font: 'Lucida Console, monospace', difficulty: 'hard' },
            { text: 'Virtual reality immerses users in digital worlds', font: 'Brush Script MT, cursive', difficulty: 'hard' },
            { text: 'Blockchain enables decentralized secure transactions', font: 'Arial Black, sans-serif', difficulty: 'hard' },
            { text: 'Cryptocurrency markets are highly volatile assets', font: 'Calibri, sans-serif', difficulty: 'hard' },
            { text: 'Non fungible tokens represent unique digital ownership', font: 'Cambria, serif', difficulty: 'hard' },
            { text: 'Metaverse platforms blend virtual and physical reality', font: 'Candara, sans-serif', difficulty: 'hard' },
            { text: 'Web3 technology promises user owned internet', font: 'Consolas, monospace', difficulty: 'hard' },
            { text: 'Decentralized finance disrupts traditional banking systems', font: 'Corbel, sans-serif', difficulty: 'hard' },
            { text: 'Smart contracts execute automatically when conditions met', font: 'Didot, serif', difficulty: 'hard' },
            { text: 'DAO communities govern through collective voting mechanisms', font: 'Franklin Gothic, sans-serif', difficulty: 'hard' },
            { text: 'Python programming language is widely used for AI', font: 'Gabriola, cursive', difficulty: 'hard' },
            { text: 'Machine learning algorithms improve with more training data', font: 'Javanese Text, sans-serif', difficulty: 'hard' },
            { text: 'Deep learning models require massive computational resources', font: 'Leelawadee, sans-serif', difficulty: 'hard' },
            { text: 'Natural language processing enables human computer interaction', font: 'Malgun Gothic, sans-serif', difficulty: 'hard' },
            { text: 'Computer vision systems can identify objects accurately', font: 'Microsoft YaHei, sans-serif', difficulty: 'hard' },
            { text: 'Robotics automation transforms manufacturing industries worldwide', font: 'Segoe UI, sans-serif', difficulty: 'hard' },
            { text: 'Internet of things connects billions of smart devices', font: 'Sylfaen, serif', difficulty: 'hard' },
            { text: 'Cybersecurity protects sensitive data from malicious attacks', font: 'Traditional Arabic, serif', difficulty: 'hard' }
        ];

        // ==================== GAME STATE ====================
        let currentDifficulty = 'easy';
        let filteredQuestions = [];
        let currentQuestionIndex = 0;
        let score = 0;
        let answers = {}; // { index: 'correct/wrong/skipped' }
        let streak = 0;
        let maxStreak = 0;
        let inputLocked = false;

        // ==================== INIT ====================
        function initGame() {
            filteredQuestions = questions.filter(q => q.difficulty === currentDifficulty);
            currentQuestionIndex = 0;
            score = 0;
            answers = {};
            streak = 0;
            maxStreak = 0;
            inputLocked = false;
            
            document.getElementById('answerInput').value = '';
            document.getElementById('answerInput').classList.remove('correct', 'wrong');
            document.getElementById('feedback').style.display = 'none';
            
            updateStats();
            loadQuestion();
            renderQuestionList();
            updateDifficultyTag();
        }

        function setDifficulty(diff) {
            currentDifficulty = diff;
            document.querySelectorAll('.difficulty-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            initGame();
        }

        function loadQuestion() {
            if (currentQuestionIndex >= filteredQuestions.length) {
                showResult();
                return;
            }

            const q = filteredQuestions[currentQuestionIndex];
            document.getElementById('questionText').style.fontFamily = q.font;
            document.getElementById('questionText').innerText = q.text;
            document.getElementById('hintBox').innerHTML = `💡 Hint: Ketik teks yang kamu lihat persis seperti ini (${q.text.length} karakter)`;
            document.getElementById('answerInput').value = '';
            document.getElementById('answerInput').classList.remove('correct', 'wrong');
            document.getElementById('feedback').style.display = 'none';
            
            // If already answered, show the answer
            if (answers[currentQuestionIndex]) {
                document.getElementById('answerInput').value = q.text;
                document.getElementById('answerInput').classList.add(
                    answers[currentQuestionIndex] === 'correct' ? 'correct' : 'wrong'
                );
                inputLocked = true;
            } else {
                inputLocked = false;
            }
            
            updateProgress();
            renderQuestionList();
        }

        function checkAnswer() {
            if (inputLocked) return;
            
            const input = document.getElementById('answerInput').value.trim();
            const q = filteredQuestions[currentQuestionIndex];
            
            if (input === '') {
                alert('Masukkan jawaban dulu!');
                return;
            }

            const isCorrect = input.toLowerCase() === q.text.toLowerCase();
            
            if (isCorrect) {
                score += 10;
                streak++;
                if (streak > maxStreak) maxStreak = streak;
                answers[currentQuestionIndex] = 'correct';
                
                document.getElementById('answerInput').classList.add('correct');
                document.getElementById('feedback').className = 'feedback correct';
                document.getElementById('feedback').innerHTML = '✅ BENAR! +10 poin';
            } else {
                streak = 0;
                answers[currentQuestionIndex] = 'wrong';
                
                document.getElementById('answerInput').classList.add('wrong');
                document.getElementById('feedback').className = 'feedback wrong';
                document.getElementById('feedback').innerHTML = `❌ SALAH! Jawaban: "${q.text}"`;
            }
            
            document.getElementById('feedback').style.display = 'block';
            inputLocked = true;
            updateStats();
            renderQuestionList();
        }

        function nextQuestion() {
            if (currentQuestionIndex < filteredQuestions.length - 1) {
                currentQuestionIndex++;
                loadQuestion();
            } else if (currentQuestionIndex === filteredQuestions.length - 1) {
                // This was the last question
                if (!answers[currentQuestionIndex]) {
                    // If not answered, maybe warn?
                }
                showResult();
            }
        }

        function skipQuestion() {
            if (inputLocked) return;
            
            answers[currentQuestionIndex] = 'skipped';
            streak = 0;
            
            document.getElementById('feedback').className = 'feedback wrong';
            document.getElementById('feedback').innerHTML = `⏭️ Dilewati. Jawaban: "${filteredQuestions[currentQuestionIndex].text}"`;
            document.getElementById('feedback').style.display = 'block';
            document.getElementById('answerInput').value = filteredQuestions[currentQuestionIndex].text;
            document.getElementById('answerInput').classList.add('wrong');
            
            inputLocked = true;
            updateStats();
            renderQuestionList();
        }

        function updateStats() {
            const total = filteredQuestions.length;
            const answered = Object.keys(answers).length;
            const correct = Object.values(answers).filter(a => a === 'correct').length;
            const accuracy = answered > 0 ? Math.round((correct / answered) * 100) : 0;
            
            document.getElementById('scoreDisplay').innerText = score;
            document.getElementById('totalDisplay').innerText = `${answered}/${total}`;
            document.getElementById('streakDisplay').innerText = streak;
            document.getElementById('accuracyDisplay').innerText = accuracy + '%';
        }

        function updateProgress() {
            const total = filteredQuestions.length;
            const answered = Object.keys(answers).length;
            const progress = (answered / total) * 100;
            
            document.getElementById('progressFill').style.width = progress + '%';
            document.getElementById('progressText').innerText = `${answered}/${total} questions`;
        }

        function renderQuestionList() {
            const list = document.getElementById('questionList');
            list.innerHTML = '';
            
            filteredQuestions.forEach((q, index) => {
                const item = document.createElement('div');
                item.className = `question-item ${index === currentQuestionIndex ? 'current' : ''}`;
                
                const status = answers[index] || 'pending';
                const statusClass = status === 'correct' ? 'status-correct' : 
                                   status === 'wrong' ? 'status-wrong' : 'status-pending';
                
                item.innerHTML = `
                    <div class="q-num">${index + 1}</div>
                    <div class="q-preview">${q.text.substring(0, 30)}${q.text.length > 30 ? '...' : ''}</div>
                    <div class="q-status ${statusClass}"></div>
                `;
                
                item.onclick = () => jumpToQuestion(index);
                list.appendChild(item);
            });
        }

        function jumpToQuestion(index) {
            if (index !== currentQuestionIndex) {
                currentQuestionIndex = index;
                loadQuestion();
            }
        }

        function updateDifficultyTag() {
            const tag = document.getElementById('currentDifficultyTag');
            tag.className = `difficulty-tag tag-${currentDifficulty}`;
            tag.innerText = currentDifficulty.toUpperCase();
        }

        function showResult() {
            const total = filteredQuestions.length;
            const correct = Object.values(answers).filter(a => a === 'correct').length;
            const wrong = Object.values(answers).filter(a => a === 'wrong').length;
            const skipped = Object.values(answers).filter(a => a === 'skipped').length;
            const accuracy = total > 0 ? Math.round((correct / total) * 100) : 0;
            
            let message = '';
            if (accuracy >= 90) message = '🌟 FONT MASTER!';
            else if (accuracy >= 70) message = '✨ GOOD JOB!';
            else if (accuracy >= 50) message = '👍 KEEP PRACTICING!';
            else message = '💪 TRY AGAIN!';
            
            document.getElementById('modalTitle').innerText = 'QUIZ COMPLETE!';
            document.getElementById('modalStats').innerHTML = `
                <div style="margin:10px 0"><strong>Score:</strong> ${score}</div>
                <div style="margin:10px 0"><strong>Correct:</strong> ${correct}/${total}</div>
                <div style="margin:10px 0"><strong>Wrong:</strong> ${wrong}</div>
                <div style="margin:10px 0"><strong>Skipped:</strong> ${skipped}</div>
                <div style="margin:10px 0"><strong>Accuracy:</strong> ${accuracy}%</div>
                <div style="margin:10px 0"><strong>Max Streak:</strong> ${maxStreak}</div>
                <div style="margin:20px 0 0 0; font-size:20px;">${message}</div>
            `;
            
            document.getElementById('resultModal').classList.add('show');
        }

        function closeModal() {
            document.getElementById('resultModal').classList.remove('show');
            initGame();
        }

        // Enter key to check answer
        document.getElementById('answerInput').addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                e.preventDefault();
                if (!inputLocked) checkAnswer();
            }
        });

        // Initialize
        initGame();

        console.log('%c🔤 DEMOX TEXT QUIZ 🔤', 'font-size: 25px; color: #667eea;');
        console.log('%c📝 Tebak TEKS-nya, bukan fontnya!', 'font-size: 14px; color: #764ba2;');
        console.log('%c🎯 100 pertanyaan • 3 difficulty', 'font-size: 14px; color: #00b09b;');
    </script>
</body>
</html>
