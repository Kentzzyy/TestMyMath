math.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Math Quiz Hub</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: Arial, sans-serif; }
        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }
        .menu-card {
            background: white;
            padding: 35px;
            border-radius: 25px;
            max-width: 450px;
            width: 100%;
            text-align: center;
            box-shadow: 0 10px 35px rgba(0,0,0,0.1);
        }
        h1 {
            color: #2d3748;
            margin-bottom: 30px;
            font-size: 28px;
        }
        .level-btn {
            width: 100%;
            padding: 20px;
            margin: 12px 0;
            border: none;
            border-radius: 15px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .level-btn:hover { transform: scale(1.03); }
        #easy { background: #48bb78; }
        #easy-mid { background: #3182ce; }
        #medium { background: #9f7aea; }
        #hard { background: #7b1fa2; }
    </style>
</head>
<body>
    <div class="menu-card">
        <h1>📚 MATH QUIZ CHALLENGE</h1>
        <button class="level-btn" id="easy" onclick="window.location.href='mathO.html'">Level 1: Easy (+, - only)</button>
        <button class="level-btn" id="easy-mid" onclick="window.location.href='math1.html'">Level 2: Easy-Mid (3+ ±)</button>
        <button class="level-btn" id="medium" onclick="window.location.href='math2.html'">Level 3: Medium (+, -, ×)</button>
        <button class="level-btn" id="hard" onclick="window.location.href='math3.html'">Level 4: Hard (×, ÷ only)</button>
    </div>
</body>
</html>

    mathO.html
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Easy Math Quiz</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #f0fff4 0%, #c6f6d5 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .quiz-card {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 8px 30px rgba(0,0,0,0.1);
        }

        h1 {
            color: #2d3748;
            margin-bottom: 25px;
            border-bottom: 3px solid #48bb78;
            padding-bottom: 15px;
        }

        #question {
            font-size: 22px;
            color: #2d3748;
            margin: 20px 0;
            padding: 15px;
            background: #f7fafc;
            border-radius: 10px;
        }

        .answer-buttons {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 25px 0;
        }

        .ans-btn {
            padding: 18px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }

        #btn-A { background: #48bb78; }
        #btn-B { background: #3182ce; }
        #btn-C { background: #ed8936; }
        #btn-D { background: #e53e3e; }
        #btn-E { background: #9f7aea; }
        #btn-F { background: #667eea; }

        .ans-btn:hover {
            transform: scale(1.05);
        }

        #feedback {
            font-size: 20px;
            font-weight: bold;
            margin: 15px 0;
        }

        .nav-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }

        .back-btn { background: #2d3748; }
        .next-btn { background: #3182ce; }
    </style>
</head>
<body>
    <div class="quiz-card">
        <h1>--- EASY MATH QUIZ ---</h1>
        <div id="question">Loading question...</div>
        <div class="answer-buttons">
            <button class="ans-btn" id="btn-A">A</button>
            <button class="ans-btn" id="btn-B">B</button>
            <button class="ans-btn" id="btn-C">C</button>
            <button class="ans-btn" id="btn-D">D</button>
            <button class="ans-btn" id="btn-E">E</button>
            <button class="ans-btn" id="btn-F">F</button>
        </div>
        <div id="feedback"></div>
        <div class="nav-buttons">
            <button class="nav-btn back-btn" onclick="window.location.href='Math.html'">I want to go back it's too difficult</button>
            <button class="nav-btn next-btn" onclick="window.location.href='math1.html'">This is too easy make it more harder!!!</button>
        </div>
    </div>

    <script>
        // Only + and -, no values <3
        function generateQuestion() {
            const op = Math.random() > 0.5 ? '+' : '-';
            let a = Math.floor(Math.random() * 20) + 3;
            let b = Math.floor(Math.random() * 20) + 3;

            if (op === '-' && a < b) [a, b] = [b, a];
            const correct = op === '+' ? a + b : a - b;
            const text = `${a} ${op} ${b} = ?`;

            // Create 5 wrong options
            const options = [correct];
            while (options.length < 6) {
                const wrong = Math.floor(Math.random() * 40) + 3;
                if (!options.includes(wrong)) options.push(wrong);
            }
            options.sort(() => Math.random() - 0.5);
            return { text, correct, options };
        }

        let currentQ;

        function loadQ() {
            currentQ = generateQuestion();
            document.getElementById('question').textContent = currentQ.text;
            document.getElementById('feedback').textContent = "";
            const btns = ['btn-A', 'btn-B', 'btn-C', 'btn-D', 'btn-E', 'btn-F'];
            btns.forEach((btnId, idx) => {
                document.getElementById(btnId).textContent = `${String.fromCharCode(65 + idx)}) ${currentQ.options[idx]}`;
            });
        }

        // Update ALL buttons to load new question after answer
        function checkAnswer(btnId) {
            const userVal = parseInt(document.getElementById(btnId).textContent.split(') ')[1]);
            const feedback = document.getElementById('feedback');
            
            if (userVal === currentQ.correct) {
                feedback.textContent = "✅ CORRECT!";
                feedback.style.color = "#48bb78";
            } else {
                feedback.textContent = `❌ WRONG! Correct = ${currentQ.correct}`;
                feedback.style.color = "#e53e3e";
            }
            // Load new question NO MATTER WHAT
            setTimeout(loadQ, 1500);
        }

        // Add click listeners
        ['btn-A', 'btn-B', 'btn-C', 'btn-D', 'btn-E', 'btn-F'].forEach(id => {
            document.getElementById(id).addEventListener('click', () => checkAnswer(id));
        });

        // Start first question
        loadQ();
    </script>
</body>
</html>


math1.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Easy-Mid Math Challenge</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .quiz-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 8px 32px rgba(0,0,0,0.15);
        }

        h1 {
            color: #2d3748;
            margin-bottom: 25px;
            border-bottom: 3px solid #3182ce;
            padding-bottom: 15px;
        }

        #question {
            font-size: 22px;
            color: #2d3748;
            margin: 20px 0;
            padding: 15px;
            background: #f7fafc;
            border-radius: 10px;
        }

        .answer-buttons {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 25px 0;
        }

        .ans-btn {
            padding: 18px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .ans-btn:hover {
            transform: scale(1.05);
        }

        #btn-A { background: #3182ce; }
        #btn-B { background: #ed8936; }
        #btn-C { background: #48bb78; }
        #btn-D { background: #e53e3e; }
        #btn-E { background: #9f7aea; }
        #btn-F { background: #f6ad55; }

        #feedback {
            font-size: 20px;
            font-weight: bold;
            margin: 15px 0;
        }

        .nav-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }

        .back-btn { background: #2d3748; }
        .harder-btn { background: #ed8936; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>--- EASY-MID MATH CHALLENGE ---</h1>
        
        <div id="question">Loading question...</div>
        
        <div class="answer-buttons">
            <button class="ans-btn" id="btn-A">A</button>
            <button class="ans-btn" id="btn-B">B</button>
            <button class="ans-btn" id="btn-C">C</button>
            <button class="ans-btn" id="btn-D">D</button>
            <button class="ans-btn" id="btn-E">E</button>
            <button class="ans-btn" id="btn-F">F</button>
        </div>

        <div id="feedback"></div>
        
        <div class="nav-buttons">
            <button class="nav-btn back-btn" onclick="window.location.href='mathO.html'">I want to go back it's too difficult</button>
            <button class="nav-btn harder-btn" onclick="window.location.href='Math2.html'">This is too easy make it harder!!!</button>
        </div>
    </div>

    <script>
        // ONLY ADDITION & SUBTRACTION | 3+ NUMBERS | NO VALUES <3
        function generateQuestion() {
            const numCount = Math.floor(Math.random() * 2) + 3; // 3-4 numbers per question
            let nums = [], ops = [], text = "", correct = 0;

            // Generate numbers ≥3
            for (let i = 0; i < numCount; i++) {
                nums.push(Math.floor(Math.random() * 25) + 3);
            }

            // Generate operations (+/- only)
            for (let i = 0; i < numCount - 1; i++) {
                ops.push(Math.random() > 0.5 ? '+' : '-');
            }

            // Build question text and calculate correct answer
            text += nums[0];
            correct = nums[0];
            for (let i = 0; i < ops.length; i++) {
                text += ` ${ops[i]} ${nums[i+1]}`;
                correct = ops[i] === '+' ? correct + nums[i+1] : correct - nums[i+1];
            }
            text += " = ?";

            // Generate 5 wrong options (all ≥3)
            const options = [correct];
            while (options.length < 6) {
                const wrong = Math.floor(Math.random() * 60) + 3;
                if (!options.includes(wrong)) options.push(wrong);
            }

            // Shuffle options
            options.sort(() => Math.random() - 0.5);

            return { text, correct, options };
        }

        let currentQ;

        function loadNewQuestion() {
            currentQ = generateQuestion();
            document.getElementById('question').textContent = currentQ.text;
            
            // Update all A-F buttons
            const buttons = ['A', 'B', 'C', 'D', 'E', 'F'];
            buttons.forEach((letter, idx) => {
                document.getElementById(`btn-${letter}`).textContent = `${letter}) ${currentQ.options[idx]}`;
            });

            document.getElementById('feedback').textContent = "";
        }

        // Check answer and load new question immediately
        function checkAnswer(btnId) {
            const letter = btnId.split('-')[1];
            const userVal = parseInt(document.getElementById(btnId).textContent.split(') ')[1]);
            const feedback = document.getElementById('feedback');

            if (userVal === currentQ.correct) {
                feedback.textContent = "✅ CORRECT!";
                feedback.style.color = "#48bb78";
            } else {
                feedback.textContent = `❌ WRONG! Correct answer is ${currentQ.correct}`;
                feedback.style.color = "#e53e3e";
            }

            // Load new question RIGHT AWAY
            setTimeout(loadNewQuestion, 1000);
        }

        // Add click listeners to all 6 buttons
        ['btn-A', 'btn-B', 'btn-C', 'btn-D', 'btn-E', 'btn-F'].forEach(id => {
            document.getElementById(id).addEventListener('click', () => checkAnswer(id));
        });

        // Start with first question
        loadNewQuestion();
    </script>
</body>
</html>


math2.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Medium Math Challenge</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #f3e5f5 0%, #ce93d8 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .quiz-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 8px 32px rgba(0,0,0,0.15);
        }

        h1 {
            color: #4a148c;
            margin-bottom: 25px;
            border-bottom: 3px solid #7b1fa2;
            padding-bottom: 15px;
        }

        #question {
            font-size: 22px;
            color: #2d3748;
            margin: 20px 0;
            padding: 15px;
            background: #f7fafc;
            border-radius: 10px;
        }

        .answer-buttons {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 25px 0;
        }

        .ans-btn {
            padding: 18px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .ans-btn:hover {
            transform: scale(1.05);
        }

        #btn-A { background: #7b1fa2; }
        #btn-B { background: #5e35b1; }
        #btn-C { background: #3949ab; }
        #btn-D { background: #283593; }
        #btn-E { background: #1a237e; }
        #btn-F { background: #0d47a1; }

        #feedback {
            font-size: 20px;
            font-weight: bold;
            margin: 15px 0;
        }

        .nav-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }

        .back-btn { background: #2d3748; }
        .menu-btn { background: #7b1fa2; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>--- MEDIUM MATH CHALLENGE ---</h1>
        
        <div id="question">Loading question...</div>
        
        <div class="answer-buttons">
            <button class="ans-btn" id="btn-A">A</button>
            <button class="ans-btn" id="btn-B">B</button>
            <button class="ans-btn" id="btn-C">C</button>
            <button class="ans-btn" id="btn-D">D</button>
            <button class="ans-btn" id="btn-E">E</button>
            <button class="ans-btn" id="btn-F">F</button>
        </div>

        <div id="feedback"></div>
        
        <div class="nav-buttons">
            <button class="nav-btn back-btn" onclick="window.location.href='math1.html'">I want to go back it's too difficult</button>
            <button class="nav-btn menu-btn" onclick="window.location.href='Math3.html'">I want x and ÷ only</button>
        </div>
    </div>

    <script>
        // 3-5 operations per question | +, -, × only | numbers 3-25
        function generateQuestion() {
            const opTypes = ['+', '-', '×'];
            const numCount = Math.floor(Math.random() * 3) + 3; // 3-5 numbers
            let nums = [], ops = [], text = "", correct = 0;

            // Generate numbers (3-25)
            for (let i = 0; i < numCount; i++) {
                nums.push(Math.floor(Math.random() * 23) + 3);
            }

            // Generate operations (1 less than number count)
            for (let i = 0; i < numCount - 1; i++) {
                ops.push(opTypes[Math.floor(Math.random() * 3)]);
            }

            // Build question text and calculate correct answer
            text += nums[0];
            correct = nums[0];
            for (let i = 0; i < ops.length; i++) {
                text += ` ${ops[i]} ${nums[i+1]}`;
                if (ops[i] === '+') correct += nums[i+1];
                else if (ops[i] === '-') correct -= nums[i+1];
                else if (ops[i] === '×') correct *= nums[i+1];
            }
            text += " = ?";

            // Generate 5 wrong options (all unique, 3-50)
            const options = [correct];
            while (options.length < 6) {
                const wrong = Math.floor(Math.random() * 48) + 3;
                if (!options.includes(wrong)) options.push(wrong);
            }

            // Shuffle options
            options.sort(() => Math.random() - 0.5);

            return { text, options, correct };
        }

        let currentQ;

        function loadNewQuestion() {
            currentQ = generateQuestion();
            document.getElementById('question').textContent = currentQ.text;
            
            // Update A-F buttons
            ['A', 'B', 'C', 'D', 'E', 'F'].forEach((letter, idx) => {
                document.getElementById(`btn-${letter}`).textContent = `${letter}) ${currentQ.options[idx]}`;
            });
            document.getElementById('feedback').textContent = "";
        }

        // Check answer and load new question
        function checkAnswer(btnId) {
            const letter = btnId.split('-')[1];
            const userVal = parseInt(document.getElementById(btnId).textContent.split(') ')[1]);
            
            if (userVal === currentQ.correct) {
                document.getElementById('feedback').textContent = "✅ CORRECT!";
                document.getElementById('feedback').style.color = "#2e7d32";
            } else {
                document.getElementById('feedback').textContent = `❌ WRONG! Correct is ${currentQ.correct}`;
                document.getElementById('feedback').style.color = "#b71c1c";
            }

            // Load new question after 1 second
            setTimeout(loadNewQuestion, 1000);
        }

        // Add click listeners to all buttons
        ['btn-A', 'btn-B', 'btn-C', 'btn-D', 'btn-E', 'btn-F'].forEach(id => {
            document.getElementById(id).addEventListener('click', () => checkAnswer(id));
        });

        // Start with first question
        loadNewQuestion();
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Medium Math Challenge</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #f3e5f5 0%, #ce93d8 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .quiz-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 8px 32px rgba(0,0,0,0.15);
        }

        h1 {
            color: #4a148c;
            margin-bottom: 25px;
            border-bottom: 3px solid #7b1fa2;
            padding-bottom: 15px;
        }

        #question {
            font-size: 22px;
            color: #2d3748;
            margin: 20px 0;
            padding: 15px;
            background: #f7fafc;
            border-radius: 10px;
        }

        .answer-buttons {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 25px 0;
        }

        .ans-btn {
            padding: 18px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .ans-btn:hover {
            transform: scale(1.05);
        }

        #btn-A { background: #7b1fa2; }
        #btn-B { background: #5e35b1; }
        #btn-C { background: #3949ab; }
        #btn-D { background: #283593; }
        #btn-E { background: #1a237e; }
        #btn-F { background: #0d47a1; }

        #feedback {
            font-size: 20px;
            font-weight: bold;
            margin: 15px 0;
        }

        .nav-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }

        .back-btn { background: #2d3748; }
        .menu-btn { background: #7b1fa2; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>--- MEDIUM MATH CHALLENGE ---</h1>
        
        <div id="question">Loading question...</div>
        
        <div class="answer-buttons">
            <button class="ans-btn" id="btn-A">A</button>
            <button class="ans-btn" id="btn-B">B</button>
            <button class="ans-btn" id="btn-C">C</button>
            <button class="ans-btn" id="btn-D">D</button>
            <button class="ans-btn" id="btn-E">E</button>
            <button class="ans-btn" id="btn-F">F</button>
        </div>

        <div id="feedback"></div>
        
        <div class="nav-buttons">
            <button class="nav-btn back-btn" onclick="window.location.href='math1.html'">I want to go back it's too difficult</button>
            <button class="nav-btn menu-btn" onclick="window.location.href='Math3.html'">I want x and ÷ only</button>
        </div>
    </div>

    <script>
        // 3-5 operations per question | +, -, × only | numbers 3-25
        function generateQuestion() {
            const opTypes = ['+', '-', '×'];
            const numCount = Math.floor(Math.random() * 3) + 3; // 3-5 numbers
            let nums = [], ops = [], text = "", correct = 0;

            // Generate numbers (3-25)
            for (let i = 0; i < numCount; i++) {
                nums.push(Math.floor(Math.random() * 23) + 3);
            }

            // Generate operations (1 less than number count)
            for (let i = 0; i < numCount - 1; i++) {
                ops.push(opTypes[Math.floor(Math.random() * 3)]);
            }

            // Build question text and calculate correct answer
            text += nums[0];
            correct = nums[0];
            for (let i = 0; i < ops.length; i++) {
                text += ` ${ops[i]} ${nums[i+1]}`;
                if (ops[i] === '+') correct += nums[i+1];
                else if (ops[i] === '-') correct -= nums[i+1];
                else if (ops[i] === '×') correct *= nums[i+1];
            }
            text += " = ?";

            // Generate 5 wrong options (all unique, 3-50)
            const options = [correct];
            while (options.length < 6) {
                const wrong = Math.floor(Math.random() * 48) + 3;
                if (!options.includes(wrong)) options.push(wrong);
            }

            // Shuffle options
            options.sort(() => Math.random() - 0.5);

            return { text, options, correct };
        }

        let currentQ;

        function loadNewQuestion() {
            currentQ = generateQuestion();
            document.getElementById('question').textContent = currentQ.text;
            
            // Update A-F buttons
            ['A', 'B', 'C', 'D', 'E', 'F'].forEach((letter, idx) => {
                document.getElementById(`btn-${letter}`).textContent = `${letter}) ${currentQ.options[idx]}`;
            });
            document.getElementById('feedback').textContent = "";
        }

        // Check answer and load new question
        function checkAnswer(btnId) {
            const letter = btnId.split('-')[1];
            const userVal = parseInt(document.getElementById(btnId).textContent.split(') ')[1]);
            
            if (userVal === currentQ.correct) {
                document.getElementById('feedback').textContent = "✅ CORRECT!";
                document.getElementById('feedback').style.color = "#2e7d32";
            } else {
                document.getElementById('feedback').textContent = `❌ WRONG! Correct is ${currentQ.correct}`;
                document.getElementById('feedback').style.color = "#b71c1c";
            }

            // Load new question after 1 second
            setTimeout(loadNewQuestion, 1000);
        }

        // Add click listeners to all buttons
        ['btn-A', 'btn-B', 'btn-C', 'btn-D', 'btn-E', 'btn-F'].forEach(id => {
            document.getElementById(id).addEventListener('click', () => checkAnswer(id));
        });

        // Start with first question
        loadNewQuestion();
    </script>
</body>
</html>


math3.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hard Math Challenge</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #ede7f6 0%, #9575cd 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .quiz-container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 8px 32px rgba(0,0,0,0.15);
        }

        h1 {
            color: #4a148c;
            margin-bottom: 25px;
            border-bottom: 3px solid #7b1fa2;
            padding-bottom: 15px;
        }

        #question {
            font-size: 22px;
            color: #2d3748;
            margin: 20px 0;
            padding: 15px;
            background: #f7fafc;
            border-radius: 10px;
        }

        .answer-buttons {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 25px 0;
        }

        .ans-btn {
            padding: 18px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .ans-btn:hover {
            transform: scale(1.05);
        }

        #btn-A { background: #7b1fa2; }
        #btn-B { background: #673ab7; }
        #btn-C { background: #5e35b1; }
        #btn-D { background: #512da8; }
        #btn-E { background: #4527a0; }
        #btn-F { background: #311b92; }

        #feedback {
            font-size: 20px;
            font-weight: bold;
            margin: 15px 0;
        }

        .nav-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }

        .back-btn { background: #2d3748; }
        .menu-btn { background: #7b1fa2; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>--- HARD MATH CHALLENGE ---</h1>
        
        <div id="question">Loading question...</div>
        
        <div class="answer-buttons">
            <button class="ans-btn" id="btn-A">A</button>
            <button class="ans-btn" id="btn-B">B</button>
            <button class="ans-btn" id="btn-C">C</button>
            <button class="ans-btn" id="btn-D">D</button>
            <button class="ans-btn" id="btn-E">E</button>
            <button class="ans-btn" id="btn-F">F</button>
        </div>

        <div id="feedback"></div>
        
        <div class="nav-buttons">
            <button class="nav-btn back-btn" onclick="window.location.href='math2.html'">I want to go back it's too difficult</button>
            <button class="nav-btn menu-btn" onclick="window.location.href='Math.html'">Back to main menu</button>
        </div>
    </div>

    <script>
        // HARD LEVEL: ONLY Multiplication & Division (no + or -)
        function generateHardQuestion() {
            const numCount = Math.floor(Math.random() * 2) + 3; // 3-4 numbers per question
            let nums = [], ops = [], text = "", correct = 0;

            // Generate numbers (5-30 range)
            for (let i = 0; i < numCount; i++) {
                nums.push(Math.floor(Math.random() * 26) + 5); // 5-30
            }

            // Generate operations (× or ÷ only)
            for (let i = 0; i < numCount - 1; i++) {
                ops.push(Math.random() > 0.5 ? '×' : '÷');
            }

            // Build question text and calculate correct answer
            text += nums[0];
            correct = nums[0];
            for (let i = 0; i < ops.length; i++) {
                text += ` ${ops[i]} ${nums[i+1]}`;
                if (ops[i] === '×') {
                    correct *= nums[i+1];
                } else {
                    // Ensure division results in whole numbers
                    while (correct % nums[i+1] !== 0) {
                        nums[i+1] = Math.floor(Math.random() * 10) + 5;
                        text = text.slice(0, text.lastIndexOf(' ')) + ` ${nums[i+1]}`;
                    }
                    correct = Math.floor(correct / nums[i+1]);
                }
            }
            text += " = ?";

            // Generate 5 wrong options (unique, whole numbers)
            const options = [correct];
            while (options.length < 6) {
                const wrong = Math.floor(Math.random() * 200) + 10; // 10-210
                if (!options.includes(wrong)) options.push(wrong);
            }
            options.sort(() => Math.random() - 0.5);

            return { text, correct, options };
        }

        let currentQ;

        function loadQuestion() {
            currentQ = generateHardQuestion();
            document.getElementById('question').textContent = currentQ.text;
            
            // Update A-F buttons
            ['A','B','C','D','E','F'].forEach((letter, idx) => {
                document.getElementById(`btn-${letter}`).textContent = `${letter}) ${currentQ.options[idx]}`;
            });
            document.getElementById('feedback').textContent = "";
        }

        function checkAnswer(btnId) {
            const userVal = parseInt(document.getElementById(btnId).textContent.split(') ')[1]);
            const feedback = document.getElementById('feedback');

            if (userVal === currentQ.correct) {
                feedback.textContent = "✅ EXCELLENT! You got it!";
                feedback.style.color = "#2e7d32";
            } else {
                feedback.textContent = `❌ WRONG! Correct answer is ${currentQ.correct}`;
                feedback.style.color = "#b71c1c";
            }
            setTimeout(loadQuestion, 1200);
        }

        // Add click listeners
        ['btn-A','btn-B','btn-C','btn-D','btn-E','btn-F'].forEach(id => {
            document.getElementById(id).addEventListener('click', () => checkAnswer(id));
        });

        // Start quiz
        loadQuestion();
    </script>
</body>
</html>
