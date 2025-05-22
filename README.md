 <!DOCTYPE html>
<html>
<head>
    <title>系统警告</title>
    <style>
        body { 
            font-family: 'Microsoft YaHei', sans-serif; 
            background: #000; 
            color: red; 
            text-align: center;
            padding-top: 100px;
        }
        .warning {
            border: 3px solid red;
            padding: 30px;
            width: 70%;
            margin: 0 auto;
            background: #111;
            animation: blink 0.5s infinite;
        }
        @keyframes blink {
            50% { border-color: #f00; box-shadow: 0 0 20px red; }
        }
        button {
            padding: 10px 25px;
            margin: 20px;
            font-size: 18px;
            cursor: pointer;
        }
        #confirm {
            background: linear-gradient(#f00, #800);
            color: white;
        }
        #cancel {
            background: linear-gradient(#0f0, #080);
        }
    </style>
</head>
<body>
    <div class="warning">
        <h1>⚠️ 检测到异常访问 ⚠️</h1>
        <p>您的设备已被标记为高风险</p>
        <div id="message">是否继续操作？</div>
        <div>
            <button id="confirm">确定</button>
            <button id="cancel">取消</button>
        </div>
    </div>

    <script>
        let count = 0;
        const messages = [
            "正在分析系统漏洞...",
            "检测到键盘记录程序...",
            "警告：IP地址已被记录",
            "最终警告：停止操作",
            "⚠️ 系统即将锁定 ⚠️",
            "3...2...1...",
            "开玩笑的啦！😜 你被我整蛊啦！"
        ];
        
        document.getElementById('confirm').addEventListener('click', function() {
            if(count < messages.length-1) {
                document.getElementById('message').innerHTML = 
                    `<span style="color:yellow">${messages[count++]}</span>`;
                this.textContent = ["继续","坚持","最后机会","真的要点？","你认真的？","算你狠"][count] || "😂";
            } else {
                document.querySelector('.warning').style.animation = "none";
                document.body.style.background = "linear-gradient(135deg, #ff0, #f80)";
                document.getElementById('message').innerHTML = 
                    `<h2>${messages[count]}</h2><p>你点击了 ${count+1} 次</p>`;
                this.style.display = "none";
                document.getElementById('cancel').textContent = "关闭";
            }
        });
        
        document.getElementById('cancel').addEventListener('click', function() {
            window.location.href = "https://www.baidu.com";
        });
    </script>
</body>
</html>