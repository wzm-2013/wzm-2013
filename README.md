<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>神秘网站</title>
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
        }
        .buttons {
            margin-top: 30px;
        }
        button {
            padding: 10px 20px;
            margin: 0 10px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            transition: all 0.3s;
        }
        #enterBtn {
            background-color: #4CAF50;
            color: white;
        }
        #exitBtn {
            background-color: #f44336;
            color: white;
        }
        button:hover {
            opacity: 0.8;
        }
        .counter {
            margin-top: 20px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="message">你为什么要打开这个网站？</h1>
        <div class="buttons">
            <button id="enterBtn">进入</button>
            <button id="exitBtn">退出</button>
        </div>
        <div class="counter" id="counter"></div>
    </div>

    <script>
        let clickCount = 0;
        const enterBtn = document.getElementById('enterBtn');
        const exitBtn = document.getElementById('exitBtn');
        const messageElement = document.getElementById('message');
        const counterElement = document.getElementById('counter');

        // 点击"进入"按钮
        enterBtn.addEventListener('click', function() {
            clickCount++;
            
            if (clickCount < 15) {
                messageElement.textContent = "我都跟你说你别进了";
            } else {
                messageElement.textContent = "带着我的密钥来找我，在我的微信里输入28369";
                enterBtn.disabled = true;
                enterBtn.textContent = "已完成";
                enterBtn.style.backgroundColor = "#cccccc";
            }
            
            counterElement.textContent = `你已经点击了 ${clickCount} 次`;
        });

        // 点击"退出"按钮
        exitBtn.addEventListener('click', function() {
            alert("你选择了退出，网站将关闭");
            window.close();
        });
    </script>
</body>
</html>
