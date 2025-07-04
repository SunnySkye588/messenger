<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8" />
    <title>跳转中...</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <script>
        // 所有 Messenger 链接 
        const links = [
            "https://m.me/61575012941767",
            "https://m.me/100092393395340", 
            "https://m.me/100092393395340",
        ];
        
        const LOCAL_KEY = "messengerAssignedIndex";
        
        function getAssignedIndex() {
            // 尝试从本地存储获取已分配的索引
            let saved = localStorage.getItem(LOCAL_KEY); 
            if (saved !== null) {
                return parseInt(saved, 10); 
            }
            
            // 检查URL参数中是否有测试索引
            const params = new URLSearchParams(window.location.search); 
            const testIndex = parseInt(params.get("test"), 10);
            
            if (!isNaN(testIndex) && testIndex >= 0 && testIndex < links.length) {
                localStorage.setItem(LOCAL_KEY, testIndex);
                return testIndex; 
            }
            
            // 随机分配一个索引
            const randomIndex = Math.floor(Math.random() * links.length); 
            localStorage.setItem(LOCAL_KEY, randomIndex);
            return randomIndex;
        }
        
        function redirect() {
            const index = getAssignedIndex(); 
            const target = links[index]; 
            window.location.href = target;
        }

        window.onload = redirect; 
    </script>
</head>
<body>
    <!-- 可以添加加载动画或提示信息 -->
    <div style="text-align: center; margin-top: 50px;">
        <p>正在跳转到 Messenger 客服...</p>
    </div>
</body>
</html>
