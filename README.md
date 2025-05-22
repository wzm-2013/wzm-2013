<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>互动挑战</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
            padding: 50px;
        }
        .container {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 600px;
            margin: 0 auto;
        }
        h1 {
            color: #333;
            margin-bottom: 30px;
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            padding: 12px 24px;
            margin: 0 10px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            transition: all 0.3s;
        }
        #continueBtn {
            background-color: #4CAF50;
            color: white;
        }
        #leaveBtn {
            background-color: #f44336;
            color: white;
        }
        button:hover {
            opacity: 0.8;
        }
        .progress {
            margin-top: 30px;
            height: 10px;
            background-color: #e0e0e0;
            border-radius: 5px;
            overflow: hidden;
        }
        #progressBar {
            height: 100%;
            width: 0%;
            background-color: #4CAF50;
            transition: width 0.3s;
        }
        .counter {
            margin-top: 15px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="message">你确定要继续吗？</h1>
        <div class="buttons">
            <button id="continueBtn">继续</button>
            <button id="leaveBtn">离开</button>
        </div>
        <div class="progress">
            <div id="progressBar"></div>
        </div>
        <div class="counter" id="counter">进度: 0/15</div>
    </div>

    <script>
        let clickCount = 0;
        const continueBtn = document.getElementById('continueBtn');
        const leaveBtn = document.getElementById('leaveBtn');
        const messageElement = document.getElementById('message');
        const counterElement = document.getElementById('counter');
        const progressBar = document.getElementById('progressBar');

        // 点击"继续"按钮
        continueBtn.addEventListener('click', function() {
            clickCount++;
            
            // 更新进度条
            const progress = (clickCount / 15) * 100;
            progressBar.style.width = `${progress}%`;
            
            // 更新计数器
            counterElement.textContent = `进度: ${clickCount}/15`;
            
            if (clickCount < 15) {
                messageElement.textContent = "你真的确定要继续吗？";
            } else {
                messageElement.textContent = "恭喜完成挑战！";
                continueBtn.disabled = true;
                continueBtn.textContent = "已完成";
                continueBtn.style.backgroundColor = "#cccccc";
                
                // 添加一些庆祝效果
                document.body.style.backgroundColor = "#e8f5e9";
                container.style.boxShadow = "0 0 20px rgba(76, 175, 80, 0.5)";
            }
        });

        // 点击"离开"按钮
        leaveBtn.addEventListener('click', function() {
            if(confirm("确定要离开吗？")) {
                window.location.href = "about:blank";
            }
        });
    </script>
</body>
</html>