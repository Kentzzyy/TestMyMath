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
