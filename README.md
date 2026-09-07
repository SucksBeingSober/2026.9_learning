<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>前端期末作业展示页面</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #6366f1;
            --primary-light: #818cf8;
            --bg-dark: #0f172a;
            --bg-card: #1e293b;
            --text-main: #f1f5f9;
            --text-sub: #94a3b8;
            --border: #334155;
            --success: #34d399;
        }

        body {
            font-family: "Segoe UI", system-ui, -apple-system, sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            min-height: 100vh;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(99,102,241,0.12) 0%, transparent 40%),
                radial-gradient(circle at 85% 70%, rgba(52,211,153,0.08) 0%, transparent 40%);
            padding: 40px 20px;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 60px;
        }

        h1 {
            font-size: 2.8rem;
            background: linear-gradient(90deg, var(--primary-light), var(--success));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom:12px;
        }

        .subtitle {
            color: var(--text-sub);
            font-size:1.1rem;
        }

        .cards-wrap {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px,1fr));
            gap:24px;
            margin-bottom:50px;
        }

        .card {
            background-color: var(--bg-card);
            border:1px solid var(--border);
            border-radius:16px;
            padding:28px;
            transition: all 0.3s ease;
            position: relative;
            overflow:hidden;
        }

        .card::before{
            content:"";
            position:absolute;
            top:0;
            left:-100%;
            width:100%;
            height:100%;
            background: linear-gradient(90deg, transparent, rgba(99,102,241,0.12), transparent);
            transition: left 0.6s;
        }

        .card:hover::before{
            left:100%;
        }

        .card:hover{
            transform: translateY(-6px);
            border-color: var(--primary);
            box-shadow: 0 12px 40px rgba(99,102,241,0.15);
        }

        .card h3{
            font-size:1.35rem;
            margin-bottom:14px;
            color: var(--primary-light);
        }

        .card p{
            color: var(--text-sub);
            line-height:1.7;
        }

        .tag-group{
            margin-top:18px;
            display:flex;
            gap:10px;
            flex-wrap:wrap;
        }

        .tag{
            font-size:0.82rem;
            padding:4px 12px;
            border-radius:999px;
            background-color:rgba(99,102,241,0.18);
            color:#c7d2fe;
        }

        .control-panel{
            background-color: var(--bg-card);
            border:1px solid var(--border);
            border-radius:16px;
            padding:30px;
            margin-bottom:40px;
        }

        .btn{
            padding:11px 22px;
            border-radius:10px;
            border:none;
            font-size:1rem;
            cursor:pointer;
            background-color: var(--primary);
            color:white;
            transition: 0.25s;
            margin:6px;
        }
        .btn:hover{
            background-color: var(--primary-light);
            transform: scale(1.04);
        }
        .btn:active{
            transform: scale(0.97);
        }

        #output-box{
            margin-top:20px;
            padding:16px;
            background:#0b1120;
            border-radius:10px;
            min-height:90px;
            color:#a5f3fc;
            font-family:Consolas,monospace;
            white-space: pre-wrap;
        }

        .animate-box{
            width:120px;
            height:120px;
            margin:24px auto;
            background:linear-gradient(135deg,var(--primary),var(--success));
            border-radius:22px;
        }

        @keyframes rotateAnim{
            0%{ transform: rotate(0deg) scale(1); }
            50%{ transform: rotate(180deg) scale(1.15); }
            100%{ transform: rotate(360deg) scale(1); }
        }
        .running{
            animation: rotateAnim 2.2s linear infinite;
        }

        footer{
            text-align:center;
            color:var(--text-sub);
            margin-top:70px;
            padding-top:24px;
            border-top:1px solid var(--border);
        }

        @media(max-width:640px){
            h1{font-size:2rem;}
            .cards-wrap{grid-template-columns:1fr;}
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>前端期末综合作业</h1>
            <p class="subtitle">HTML + CSS + JavaScript 单文件演示项目</p>
        </header>

        <div class="cards-wrap">
            <div class="card">
                <h3>🎨 样式能力</h3>
                <p>CSS变量管理主题、渐变背景、hover悬浮动效、卡片流光过渡动画、响应式网格布局，适配手机和电脑屏幕。</p>
                <div class="tag-group">
                    <span class="tag">CSS Variable</span>
                    <span class="tag">Grid</span>
                    <span class="tag">Animation</span>
                </div>
            </div>
            <div class="card">
                <h3>⚡ JS交互</h3>
                <p>按钮事件响应、DOM动态输出、状态切换、定时器动画控制，纯原生JS，不引入任何第三方库。</p>
                <div class="tag-group">
                    <span class="tag">原生JS</span>
                    <span class="tag">DOM</span>
                    <span class="tag">setInterval</span>
                </div>
            </div>
            <div class="card">
                <h3>📱 响应式</h3>
                <p>使用auto-fit网格与媒体查询，在手机、平板、电脑不同尺寸下自动调整布局，保证浏览体验。</p>
                <div class="tag-group">
                    <span class="tag">RWD</span>
                    <span class="tag">Media Query</span>
                </div>
            </div>
        </div>

        <div class="control-panel">
            <h3>🧪 JS交互演示区</h3>
            <div>
                <button class="btn" id="btnStart">开启方块动画</button>
                <button class="btn" id="btnStop">停止方块动画</button>
                <button class="btn" id="btnPrint">输出当前时间</button>
            </div>
            <div class="animate-box" id="box"></div>
            <div id="output-box">// 点击上方按钮，内容会打印在这里</div>
        </div>

        <footer>
            <p>2026 前端期末作业 · 全部代码位于单个HTML文件</p>
        </footer>
    </div>

<script>
    // 获取DOM元素
    const boxDom = document.getElementById('box');
    const outputDom = document.getElementById('output-box');
    const btnStart = document.getElementById('btnStart');
    const btnStop = document.getElementById('btnStop');
    const btnPrint = document.getElementById('btnPrint');

    let timer = null;

    // 开启动画
    btnStart.addEventListener('click', ()=>{
        boxDom.classList.add('running');
        printLog("✅ 动画已经启动");
    })

    // 停止动画
    btnStop.addEventListener('click', ()=>{
        boxDom.classList.remove('running');
        printLog("🛑 动画已经停止");
    })

    // 打印当前时间
    btnPrint.addEventListener('click', ()=>{
        const now = new Date().toLocaleString("zh-CN");
        printLog(`🕒 当前系统时间：${now}`);
    })

    // 日志输出函数
    function printLog(text){
        outputDom.innerText = text;
    }

    // 页面加载完成提示
    window.addEventListener('DOMContentLoaded',()=>{
        printLog("✅页面DOM全部加载完毕，可以开始交互");
    })
</script>
</body>
</html>
