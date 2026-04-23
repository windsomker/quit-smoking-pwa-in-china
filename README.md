# quit-smoking-pwa-in-china
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="theme-color" content="#4CAF50">
    <title>戒烟计划助手</title>
    <link rel="manifest" href="manifest.json">
    <link rel="stylesheet" href="styles.css">
    <link rel="icon" href="icons/icon-192x192.png">
    <!-- PWA iOS支持 -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="apple-mobile-web-app-title" content="戒烟助手">
    <link rel="apple-touch-icon" href="icons/icon-192x192.png">
</head>
<body>
    <!-- 导航栏 -->
    <nav class="navbar">
        <div class="container">
            <h1 class="app-title">🚭 戒烟计划助手</h1>
            <button id="installBtn" class="btn-install">安装应用</button>
        </div>
    </nav>

    <!-- 主内容 -->
    <main class="container">
        <!-- 概览卡片 -->
        <section class="card overview-card">
            <h2>戒烟进度概览</h2>
            <div class="stats-grid">
                <div class="stat-item">
                    <div class="stat-value" id="daysQuit">0</div>
                    <div class="stat-label">戒烟天数</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value" id="moneySaved">¥0</div>
                    <div class="stat-label">节省金额</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value" id="cigarettesAvoided">0</div>
                    <div class="stat-label">避免吸烟</div>
                </div>
            </div>
        </section>

        <!-- 今日鼓励 -->
        <section class="card encouragement-card">
            <h2>今日鼓励</h2>
            <p id="encouragementText">点击按钮获取鼓励语</p>
            <button id="getEncouragement" class="btn-primary">获取鼓励</button>
        </section>

        <!-- 快速记录 -->
        <section class="card quick-record-card">
            <h2>快速记录</h2>
            <div class="record-buttons">
                <button class="btn-record" data-type="craving">
                    <span>💭</span>
                    <span>记录渴望</span>
                </button>
                <button class="btn-record" data-type="mood">
                    <span>😊</span>
                    <span>记录心情</span>
                </button>
                <button class="btn-record" data-type="achievement">
                    <span>🏆</span>
                    <span>记录成就</span>
                </button>
            </div>
        </section>

        <!-- 健康益处 -->
        <section class="card health-benefits-card">
            <h2>健康益处时间线</h2>
            <div class="timeline">
                <div class="timeline-item" data-days="0">
                    <div class="timeline-time">20分钟</div>
                    <div class="timeline-content">心率和血压开始下降</div>
                </div>
                <div class="timeline-item" data-days="1">
                    <div class="timeline-time">12小时</div>
                    <div class="timeline-content">血液中一氧化碳恢复正常</div>
                </div>
                <div class="timeline-item" data-days="3">
                    <div class="timeline-time">2-3天</div>
                    <div class="timeline-content">尼古丁完全排出体外</div>
                </div>
                <div class="timeline-item" data-days="14">
                    <div class="timeline-time">2周</div>
                    <div class="timeline-content">肺功能开始改善</div>
                </div>
                <div class="timeline-item" data-days="30">
                    <div class="timeline-time">1个月</div>
                    <div class="timeline-content">冠心病风险开始下降</div>
                </div>
            </div>
        </section>

        <!-- 应对策略 -->
        <section class="card coping-strategies-card">
            <h2>应对策略</h2>
            <div class="strategies">
                <div class="strategy-category">
                    <h3>当渴望来临时</h3>
                    <ul>
                        <li>深呼吸10次</li>
                        <li>喝一杯水</li>
                        <li>嚼无糖口香糖</li>
                        <li>起身散步5分钟</li>
                    </ul>
                </div>
                <div class="strategy-category">
                    <h3>感到焦虑时</h3>
                    <ul>
                        <li>进行5分钟冥想</li>
                        <li>听舒缓音乐</li>
                        <li>做轻度伸展运动</li>
                        <li>写日记记录感受</li>
                    </ul>
                </div>
            </div>
            <button id="randomStrategy" class="btn-secondary">随机策略</button>
        </section>

        <!-- 设置 -->
        <section class="card settings-card">
            <h2>设置</h2>
            <div class="settings-form">
                <div class="form-group">
                    <label for="quitDate">戒烟开始日期：</label>
                    <input type="date" id="quitDate">
                </div>
                <div class="form-group">
                    <label for="cigarettesPerDay">原来每天吸烟数量：</label>
                    <input type="number" id="cigarettesPerDay" value="20" min="1" max="100">
                </div>
                <div class="form-group">
                    <label for="pricePerPack">每包烟价格（元）：</label>
                    <input type="number" id="pricePerPack" value="20" min="1" step="0.1">
                </div>
                <div class="form-group">
                    <label for="cigarettesPerPack">每包含烟数量：</label>
                    <input type="number" id="cigarettesPerPack" value="20" min="1">
                </div>
                <button id="saveSettings" class="btn-primary">保存设置</button>
            </div>
        </section>
    </main>

    <!-- 底部导航 -->
    <nav class="bottom-nav">
        <button class="nav-btn active" data-page="overview">
            <span>📊</span>
            <span>概览</span>
        </button>
        <button class="nav-btn" data-page="record">
            <span>📝</span>
            <span>记录</span>
        </button>
        <button class="nav-btn" data-page="progress">
            <span>📈</span>
            <span>进度</span>
        </button>
        <button class="nav-btn" data-page="settings">
            <span>⚙️</span>
            <span>设置</span>
        </button>
    </nav>

    <!-- 模态框 -->
    <div id="recordModal" class="modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h3 id="modalTitle">记录</h3>
            <div id="modalBody">
                <!-- 动态内容 -->
            </div>
        </div>
    </div>

    <!-- 通知 -->
    <div id="notification" class="notification"></div>

    <script src="app.js"></script>
</body>
</html>
/* 基础样式 */
:root {
    --primary-color: #4CAF50;
    --secondary-color: #2196F3;
    --accent-color: #FF9800;
    --background-color: #f5f5f5;
    --card-color: #ffffff;
    --text-primary: #212121;
    --text-secondary: #757575;
    --border-radius: 12px;
    --shadow: 0 2px 10px rgba(0,0,0,0.1);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background-color: var(--background-color);
    color: var(--text-primary);
    line-height: 1.6;
    padding-bottom: 80px; /* 为底部导航留空间 */
}

.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 16px;
}

/* 导航栏 */
.navbar {
    background-color: var(--primary-color);
    color: white;
    padding: 12px 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

.navbar .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.app-title {
    font-size: 1.2rem;
    font-weight: bold;
}

.btn-install {
    background-color: rgba(255, 255, 255, 0.2);
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 0.9rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btn-install:hover {
    background-color: rgba(255, 255, 255, 0.3);
}

/* 卡片样式 */
.card {
    background-color: var(--card-color);
    border-radius: var(--border-radius);
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: var(--shadow);
}

.card h2 {
    margin-bottom: 16px;
    color: var(--text-primary);
    font-size: 1.3rem;
}

/* 统计网格 */
.stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    text-align: center;
}

.stat-item {
    padding: 12px;
}

.stat-value {
    font-size: 1.8rem;
    font-weight: bold;
    color: var(--primary-color);
    margin-bottom: 4px;
}

.stat-label {
    font-size: 0.9rem;
    color: var(--text-secondary);
}

/* 按钮样式 */
.btn-primary {
    background-color: var(--primary-color);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
    width: 100%;
    margin-top: 12px;
    transition: background-color 0.3s;
}

.btn-primary:hover {
    background-color: #45a049;
}

.btn-secondary {
    background-color: var(--secondary-color);
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    font-size: 0.9rem;
    cursor: pointer;
    margin-top: 12px;
}

.btn-record {
    background-color: var(--background-color);
    border: 2px solid var(--primary-color);
    border-radius: 8px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    transition: all 0.3s;
    flex: 1;
}

.btn-record:hover {
    background-color: var(--primary-color);
    color: white;
}

.record-buttons {
    display: flex;
    gap: 12px;
    justify-content: space-between;
}

/* 时间线 */
.timeline {
    position: relative;
    padding-left: 20px;
}

.timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 2px;
    background-color: var(--primary-color);
}

.timeline-item {
    position: relative;
    padding-bottom: 20px;
}

.timeline-item::before {
    content: '';
    position: absolute;
    left: -25px;
    top: 0;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: var(--primary-color);
    border: 2px solid white;
}

.timeline-time {
    font-weight: bold;
    color: var(--primary-color);
    margin-bottom: 4px;
}

.timeline-content {
    color: var(--text-secondary);
}

/* 应对策略 */
.strategies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin-bottom: 16px;
}

.strategy-category h3 {
    color: var(--secondary-color);
    margin-bottom: 8px;
    font-size: 1.1rem;
}

.strategy-category ul {
    list-style-type: none;
    padding-left: 0;
}

.strategy-category li {
    padding: 4px 0;
    color: var(--text-secondary);
    position: relative;
    padding-left: 20px;
}

.strategy-category li::before {
    content: '•';
    position: absolute;
    left: 0;
    color: var(--accent-color);
}

/* 设置表单 */
.settings-form {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.form-group label {
    font-weight: 500;
    color: var(--text-primary);
}

.form-group input {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 6px;
    font-size: 1rem;
}

/* 底部导航 */
.bottom-nav {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: white;
    display: flex;
    justify-content: space-around;
    padding: 12px 0;
    border-top: 1px solid #eee;
    z-index: 100;
}

.nav-btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 8px;
    font-size: 0.8rem;
    transition: color 0.3s;
}

.nav-btn.active {
    color: var(--primary-color);
}

.nav-btn span:first-child {
    font-size: 1.2rem;
}

/* 模态框 */
.modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.5);
    z-index: 1000;
    align-items: center;
    justify-content: center;
}

.modal-content {
    background-color: white;
    border-radius: var(--border-radius);
    width: 90%;
    max-width: 500px;
    max-height: 80vh;
    overflow-y: auto;
    padding: 24px;
    position: relative;
}

.close-modal {
    position: absolute;
    top: 16px;
    right: 16px;
    font-size: 1.5rem;
    cursor: pointer;
    color: var(--text-secondary);
}

/* 通知 */
.notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: var(--primary-color);
    color: white;
    padding: 12px 24px;
    border-radius: 8px;
    box-shadow: var(--shadow);
    display: none;
    z-index: 1001;
}

/* 响应式设计 */
@media (max-width: 600px) {
    .stats-grid {
        grid-template-columns: 1fr;
    }
    
    .strategies {
        grid-template-columns: 1fr;
    }
    
    .record-buttons {
        flex-direction: column;
    }
}

/* 离线状态指示 */
.offline-indicator {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: #ff9800;
    color: white;
    text-align: center;
    padding: 8px;
    display: none;
    z-index: 1002;
}
/* 基础样式 */
:root {
    --primary-color: #4CAF50;
    --secondary-color: #2196F3;
    --accent-color: #FF9800;
    --background-color: #f5f5f5;
    --card-color: #ffffff;
    --text-primary: #212121;
    --text-secondary: #757575;
    --border-radius: 12px;
    --shadow: 0 2px 10px rgba(0,0,0,0.1);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background-color: var(--background-color);
    color: var(--text-primary);
    line-height: 1.6;
    padding-bottom: 80px; /* 为底部导航留空间 */
}

.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 16px;
}

/* 导航栏 */
.navbar {
    background-color: var(--primary-color);
    color: white;
    padding: 12px 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

.navbar .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.app-title {
    font-size: 1.2rem;
    font-weight: bold;
}

.btn-install {
    background-color: rgba(255, 255, 255, 0.2);
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 0.9rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btn-install:hover {
    background-color: rgba(255, 255, 255, 0.3);
}

/* 卡片样式 */
.card {
    background-color: var(--card-color);
    border-radius: var(--border-radius);
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: var(--shadow);
}

.card h2 {
    margin-bottom: 16px;
    color: var(--text-primary);
    font-size: 1.3rem;
}

/* 统计网格 */
.stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    text-align: center;
}

.stat-item {
    padding: 12px;
}

.stat-value {
    font-size: 1.8rem;
    font-weight: bold;
    color: var(--primary-color);
    margin-bottom: 4px;
}

.stat-label {
    font-size: 0.9rem;
    color: var(--text-secondary);
}

/* 按钮样式 */
.btn-primary {
    background-color: var(--primary-color);
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
    width: 100%;
    margin-top: 12px;
    transition: background-color 0.3s;
}

.btn-primary:hover {
    background-color: #45a049;
}

.btn-secondary {
    background-color: var(--secondary-color);
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    font-size: 0.9rem;
    cursor: pointer;
    margin-top: 12px;
}

.btn-record {
    background-color: var(--background-color);
    border: 2px solid var(--primary-color);
    border-radius: 8px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    transition: all 0.3s;
    flex: 1;
}

.btn-record:hover {
    background-color: var(--primary-color);
    color: white;
}

.record-buttons {
    display: flex;
    gap: 12px;
    justify-content: space-between;
}

/* 时间线 */
.timeline {
    position: relative;
    padding-left: 20px;
}

.timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 2px;
    background-color: var(--primary-color);
}

.timeline-item {
    position: relative;
    padding-bottom: 20px;
}

.timeline-item::before {
    content: '';
    position: absolute;
    left: -25px;
    top: 0;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: var(--primary-color);
    border: 2px solid white;
}

.timeline-time {
    font-weight: bold;
    color: var(--primary-color);
    margin-bottom: 4px;
}

.timeline-content {
    color: var(--text-secondary);
}

/* 应对策略 */
.strategies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin-bottom: 16px;
}

.strategy-category h3 {
    color: var(--secondary-color);
    margin-bottom: 8px;
    font-size: 1.1rem;
}

.strategy-category ul {
    list-style-type: none;
    padding-left: 0;
}

.strategy-category li {
    padding: 4px 0;
    color: var(--text-secondary);
    position: relative;
    padding-left: 20px;
}

.strategy-category li::before {
    content: '•';
    position: absolute;
    left: 0;
    color: var(--accent-color);
}

/* 设置表单 */
.settings-form {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.form-group label {
    font-weight: 500;
    color: var(--text-primary);
}

.form-group input {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 6px;
    font-size: 1rem;
}

/* 底部导航 */
.bottom-nav {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: white;
    display: flex;
    justify-content: space-around;
    padding: 12px 0;
    border-top: 1px solid #eee;
    z-index: 100;
}

.nav-btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 8px;
    font-size: 0.8rem;
    transition: color 0.3s;
}

.nav-btn.active {
    color: var(--primary-color);
}

.nav-btn span:first-child {
    font-size: 1.2rem;
}

/* 模态框 */
.modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.5);
    z-index: 1000;
    align-items: center;
    justify-content: center;
}

.modal-content {
    background-color: white;
    border-radius: var(--border-radius);
    width: 90%;
    max-width: 500px;
    max-height: 80vh;
    overflow-y: auto;
    padding: 24px;
    position: relative;
}

.close-modal {
    position: absolute;
    top: 16px;
    right: 16px;
    font-size: 1.5rem;
    cursor: pointer;
    color: var(--text-secondary);
}

/* 通知 */
.notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: var(--primary-color);
    color: white;
    padding: 12px 24px;
    border-radius: 8px;
    box-shadow: var(--shadow);
    display: none;
    z-index: 1001;
}

/* 响应式设计 */
@media (max-width: 600px) {
    .stats-grid {
        grid-template-columns: 1fr;
    }
    
    .strategies {
        grid-template-columns: 1fr;
    }
    
    .record-buttons {
        flex-direction: column;
    }
}

/* 离线状态指示 */
.offline-indicator {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: #ff9800;
    color: white;
    text-align: center;
    padding: 8px;
    display: none;
    z-index: 1002;
}
// 戒烟计划PWA应用 - 主逻辑

class QuitSmokingApp {
    constructor() {
        this.data = {
            quitDate: localStorage.getItem('quitDate') || new Date().toISOString().split('T')[0],
            cigarettesPerDay: parseInt(localStorage.getItem('cigarettesPerDay')) || 20,
            pricePerPack: parseFloat(localStorage.getItem('pricePerPack')) || 20,
            cigarettesPerPack: parseInt(localStorage.getItem('cigarettesPerPack')) || 20,
            records: JSON.parse(localStorage.getItem('records')) || []
        };
        
        this.encouragements = [
            "坚持下去！每一分钟不吸烟都是胜利。",
            "你的健康正在逐渐恢复，继续保持！",
            "省下的钱可以用来做更有意义的事情。",
            "你的肺正在感谢你，呼吸会越来越顺畅。",
            "戒烟的每一天都让你离健康更近一步。",
            "你已经证明了自己有强大的意志力！",
            "想象一下一个月后的自己，会为今天的坚持感到骄傲。",
            "每一次拒绝吸烟，都是在投资自己的未来。"
        ];
        
        this.copingStrategies = {
            craving: [
                "深呼吸10次，慢慢呼气",
                "喝一大杯水",
                "嚼无糖口香糖",
                "起身散步5分钟",
                "给支持你的朋友发信息"
            ],
            anxiety: [
                "进行5分钟冥想",
                "听舒缓音乐",
                "做轻度伸展运动",
                "写日记记录感受",
                "洗个温水脸"
            ],
            social: [
                "提前告知朋友你正在戒烟",
                "手里拿杯饮料",
                "避开吸烟区域",
                "准备拒绝吸烟的礼貌说法"
            ]
        };
        
        this.init();
    }
    
    init() {
        // 初始化事件监听
        this.initEventListeners();
        
        // 更新显示
        this.updateDisplay();
        
        // 检查PWA安装
        this.checkPWAInstall();
        
        // 注册Service Worker
        this.registerServiceWorker();
    }
    
    initEventListeners() {
        // 获取鼓励按钮
        document.getElementById('getEncouragement').addEventListener('click', () => {
            this.showRandomEncouragement();
        });
        
        // 记录按钮
        document.querySelectorAll('.btn-record').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const type = e.currentTarget.dataset.type;
                this.openRecordModal(type);
            });
        });
        
        // 随机策略按钮
        document.getElementById('randomStrategy').addEventListener('click', () => {
            this.showRandomStrategy();
        });
        
        // 保存设置按钮
        document.getElementById('saveSettings').addEventListener('click', () => {
            this.saveSettings();
        });
        
        // 安装按钮
        document.getElementById('installBtn').addEventListener('click', () => {
            this.promptPWAInstall();
        });
        
        // 关闭模态框
        document.querySelector('.close-modal').addEventListener('click', () => {
            this.closeModal();
        });
        
        // 点击模态框外部关闭
        document.getElementById('recordModal').addEventListener('click', (e) => {
            if (e.target.id === 'recordModal') {
                this.closeModal();
            }
        });
        
        // 底部导航
        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const page = e.currentTarget.dataset.page;
                this.switchPage(page);
            });
        });
    }
    
    updateDisplay() {
        // 计算戒烟天数
        const quitDate = new Date(this.data.quitDate);
        const today = new Date();
        const timeDiff = today.getTime() - quitDate.getTime();
        const daysQuit = Math.floor(timeDiff / (1000 * 3600 * 24));
        
        // 计算节省金额
        const packsPerDay = this.data.cigarettesPerDay / this.data.cigarettesPerPack;
        const moneySaved = packsPerDay * this.data.pricePerPack * daysQuit;
        
        // 计算避免的香烟数量
        const cigarettesAvoided = this.data.cigarettesPerDay * daysQuit;
        
        // 更新UI
        document.getElementById('daysQuit').textContent = daysQuit;
        document.getElementById('moneySaved').textContent = `¥${moneySaved.toFixed(2)}`;
        document.getElementById('cigarettesAvoided').textContent = cigarettesAvoided;
        
        // 更新健康益处时间线
        this.updateHealthTimeline(daysQuit);
        
        // 更新设置表单
        document.getElementById('quitDate').value = this.data.quitDate;
        document.getElementById('cigarettesPerDay').value = this.data.cigarettesPerDay;
        document.getElementById('pricePerPack').value = this.data.pricePerPack;
        document.getElementById('cigarettesPerPack').value = this.data.cigarettesPerPack;
    }
    
    updateHealthTimeline(daysQuit) {
        document.querySelectorAll('.timeline-item').forEach(item => {
            const requiredDays = parseInt(item.dataset.days);
            if (daysQuit >= requiredDays) {
                item.classList.add('achieved');
                item.style.opacity = '1';
            } else {
                item.classList.remove('achieved');
                item.style.opacity = '0.6';
            }
        });
    }
    
    showRandomEncouragement() {
        const randomIndex = Math.floor(Math.random() * this.encouragements.length);
        const encouragement = this.encouragements[randomIndex];
        document.getElementById('encouragementText').textContent = encouragement;
        this.showNotification('获取鼓励成功！');
    }
    
    showRandomStrategy() {
        const allStrategies = Object.values(this.copingStrategies).flat();
        const randomIndex = Math.floor(Math.random() * allStrategies.length);
        const strategy = allStrategies[randomIndex];
        this.showNotification(`试试这个方法：${strategy}`);
    }
    
    openRecordModal(type) {
        const modal = document.getElementById('recordModal');
        const modalTitle = document.getElementById('modalTitle');
        const modalBody = document.getElementById('modalBody');
        
        let title = '';
        let content = '';
        
        switch(type) {
            case 'craving':
                title = '记录渴望';
                content = this.createCravingForm();
                break;
            case 'mood':
                title = '记录心情';
                content = this.createMoodForm();
                break;
            case 'achievement':
                title = '记录成就';
                content = this.createAchievementForm();
                break;
        }
        
        modalTitle.textContent = title;
        modalBody.innerHTML = content;
        modal.style.display = 'flex';
        
        // 为表单添加事件监听
        this.initRecordForm(type);
    }
    
    createCravingForm() {
        return `
            <form id="cravingForm">
                <div class="form-group">
                    <label>渴望强度 (1-10):</label>
                    <input type="range" id="cravingIntensity" min="1" max="10" value="5">
                    <div class="intensity-display">
                        <span>轻度</span>
                        <span id="intensityValue">5</span>
                        <span>重度</span>
                    </div>
                </div>
                <div class="form-group">
                    <label>时间:</label>
                    <input type="time" id="cravingTime" value="${new Date().toTimeString().slice(0,5)}">
                </div>
                <div class="form-group">
                    <label>情境:</label>
                    <select id="cravingSituation">
                        <option value="morning">早晨起床</option>
                        <option value="afterMeal">饭后</option>
                        <option value="stress">压力大时</option>
                        <option value="social">社交场合</option>
                        <option value="bored">无聊时</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>使用的应对策略:</label>
                    <textarea id="cravingStrategy" rows="3" placeholder="描述你如何应对这次渴望..."></textarea>
                </div>
                <button type="submit" class="btn-primary">保存记录</button>
            </form>
        `;
    }
    
    createMoodForm() {
        return `
            <form id="moodForm">
                <div class="form-group">
                    <label>当前心情:</label>
                    <div class="mood-options">
                        <label class="mood-option">
                            <input type="radio" name="mood" value="happy">
                            <span>😊 开心</span>
                        </label>
                        <label class="mood-option">
                            <input type="radio" name="mood" value="neutral">
                            <span>😐 一般</span>
                        </label>
                        <label class="mood-option">
                            <input type="radio" name="mood" value="anxious">
                            <span>😰 焦虑</span>
                        </label>
                        <label class="mood-option">
                            <input type="radio" name="mood" value="irritable">
                            <span>😠 烦躁</span>
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label>备注:</label>
                    <textarea id="moodNote" rows="3" placeholder="描述你的感受..."></textarea>
                </div>
                <button type="submit" class="btn-primary">保存心情</button>
            </form>
        `;
    }
    
    createAchievementForm() {
        return `
            <form id="achievementForm">
                <div class="form-group">
                    <label>成就类型:</label>
                    <select id="achievementType">
                        <option value="resisted">成功抵抗渴望</option>
                        <option value="milestone">达到里程碑</option>
                        <option value="health">感受到健康改善</option>
                        <option value="savedMoney">省下可观金额</option>
                        <option value="other">其他成就</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>成就描述:</label>
                    <textarea id="achievementDescription" rows="4" placeholder="详细描述你的成就..."></textarea>
                </div>
                <div class="form-group">
                    <label>奖励自己:</label>
                    <input type="text" id="achievementReward" placeholder="打算如何奖励自己？">
                </div>
                <button type="submit" class="btn-primary">记录成就</button>
            </form>
        `;
    }
    
    initRecordForm(type) {
        const form = document.querySelector(`#${type}Form`);
        if (form) {
            form.addEventListener('submit', (e) => {
                e.preventDefault();
                this.saveRecord(type);
            });
        }
        
        // 为渴望强度滑块添加实时显示
        const intensitySlider = document.getElementById('cravingIntensity');
        const intensityValue = document.getElementById('intensityValue');
        if (intensitySlider && intensityValue) {
            intensitySlider.addEventListener('input', (e) => {
                intensityValue.textContent = e.target.value;
            });
        }
    }
    
    saveRecord(type) {
        const record = {
            type: type,
            date: new Date().toISOString(),
            timestamp: Date.now()
        };
        
        switch(type) {
            case 'craving':
                record.intensity = document.getElementById('cravingIntensity').value;
                record.time = document.getElementById('cravingTime').value;
                record.situation = document.getElementById('cravingSituation').value;
                record.strategy = document.getElementById('cravingStrategy').value;
                break;
            case 'mood':
                const moodRadio = document.querySelector('input[name="mood"]:checked');
                record.mood = moodRadio ? moodRadio.value : 'neutral';
                record.note = document.getElementById('moodNote').value;
                break;
            case 'achievement':
                record.achievementType = document.getElementById('achievementType').value;
                record.description = document.getElementById('achievementDescription').value;
                record.reward = document.getElementById('achievementReward').value;
                break;
        }
        
        this.data.records.push(record);
        this.saveToLocalStorage();
        this.closeModal();
        this.showNotification('记录保存成功！');
    }
    
    saveSettings() {
        this.data.quitDate = document.getElementById('quitDate').value;
        this.data.cigarettesPerDay = parseInt(document.getElementById('cigarettesPerDay').value);
        this.data.pricePerPack = parseFloat(document.getElementById('pricePerPack').value);
        this.data.cigarettesPerPack = parseInt(document.getElementById('cigarettesPerPack').value);
        
        this.saveToLocalStorage();
        this.updateDisplay();
        this.showNotification('设置保存成功！');
    }
    
    saveToLocalStorage() {
        localStorage.setItem('quitDate', this.data.quitDate);
        localStorage.setItem('cigarettesPerDay', this.data.cigarettesPerDay);
        localStorage.setItem('pricePerPack', this.data.pricePerPack);
        localStorage.setItem('cigarettesPerPack', this.data.cigarettesPerPack);
        localStorage.setItem('records', JSON.stringify(this.data.records));
    }
    
    closeModal() {
        document.getElementById('recordModal').style.display = 'none';
    }
    
    switchPage(page) {
        // 更新导航按钮状态
        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.classList.remove('active');
            if (btn.dataset.page === page) {
                btn.classList.add('active');
            }
        });
        
        // 这里可以添加页面切换逻辑
        this.showNotification(`切换到${page}页面`);
    }
    
    showNotification(message) {
        const notification = document.getElementById('notification');
        notification.textContent = message;
        notification.style.display = 'block';
        
        setTimeout(() => {
            notification.style.display = 'none';
        }, 3000);
    }
    
    // PWA相关功能
    checkPWAInstall() {
        // 检查是否已安装
        if (window.matchMedia('(display-mode: standalone)').matches) {
            document.getElementById('installBtn').style.display = 'none';
        }
    }
    
    promptPWAInstall() {
        // 触发PWA安装提示
        if (window.deferredPrompt) {
            window.deferredPrompt.prompt();
            window.deferredPrompt.userChoice.then((choiceResult) => {
                if (choiceResult.outcome === 'accepted') {
                    console.log('用户接受了PWA安装');
                    document.getElementById('installBtn').style.display = 'none';
                }
                window.deferredPrompt = null;
            });
        }
    }
    
    registerServiceWorker() {
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('service-worker.js')
                    .then(registration => {
                        console.log('ServiceWorker注册成功:', registration.scope);
                    })
                    .catch(error => {
                        console.log('ServiceWorker注册失败:', error);
                    });
            });
        }
    }
}

// 初始化应用
let app;
window.addEventListener('DOMContentLoaded', () => {
    app = new QuitSmokingApp();
    
    // 监听PWA安装提示
    window.addEventListener('beforeinstallprompt', (e) => {
        e.preventDefault();
        window.deferredPrompt = e;
        document.getElementById('installBtn').style.display = 'block';
    });
    
    // 监听PWA安装完成
    window.addEventListener('appinstalled', () => {
        console.log('PWA已安装');
        document.getElementById('installBtn').style.display = 'none';
        window.deferredPrompt = null;
    });
    
    // 监听网络状态
    window.addEventListener('online', () => {
        document.querySelector('.offline-indicator').style.display = 'none';
    });
    
    window.addEventListener('offline', () => {
        document.querySelector('.offline-indicator').style.display = 'block';
        document.querySelector('.offline-indicator').textContent = '当前处于离线状态';
    });
});
// Service Worker for Quit Smoking PWA

const CACHE_NAME = 'quit-smoking-v1';
const urlsToCache = [
    '/',
    '/index.html',
    '/styles.css',
    '/app.js',
    '/manifest.json',
    '/icons/icon-72x72.png',
    '/icons/icon-96x96.png',
    '/icons/icon-128x128.png',
    '/icons/icon-144x144.png',
    '/icons/icon-152x152.png',
    '/icons/icon-192x192.png',
    '/icons/icon-384x384.png',
    '/icons/icon-512x512.png'
];

// 安装Service Worker
self.addEventListener('install', event => {
    event.waitUntil(
        caches.open(CACHE_NAME)
            .then(cache => {
                console.log('缓存已打开');
                return cache.addAll(urlsToCache);
            })
    );
});

// 激活Service Worker
self.addEventListener('activate', event => {
    event.waitUntil(
        caches.keys().then(cacheNames => {
            return Promise.all(
                cacheNames.map(cacheName => {
                    if (cacheName !== CACHE_NAME) {
                        console.log('删除旧缓存:', cacheName);
                        return caches.delete(cacheName);
                    }
                })
            );
        })
    );
});

// 拦截网络请求
self.addEventListener('fetch', event => {
    event.respondWith(
        caches.match(event.request)
            .then(response => {
                // 如果缓存中有，返回缓存内容
                if (response) {
                    return response;
                }
                
                // 否则从网络获取
                return fetch(event.request)
                    .then(response => {
                        // 检查是否有效响应
                        if (!response || response.status !== 200 || response.type !== 'basic') {
                            return response;
                        }
                        
                        // 克隆响应
                        const responseToCache = response.clone();
                        
                        // 将新资源添加到缓存
                        caches.open(CACHE_NAME)
                            .then(cache => {
                                cache.put(event.request, responseToCache);
                            });
                        
                        return response;
                    })
                    .catch(() => {
                        // 网络请求失败时，可以返回一个离线页面
                        return caches.match('/index.html');
                    });
            })
    );
});

// 后台同步（如果需要）
self.addEventListener('sync', event => {
    if (event.tag === 'sync-records') {
        event.waitUntil(syncRecords());
    }
});

// 推送通知（如果需要）
self.addEventListener('push', event => {
    const options = {
        body: event.data.text(),
        icon: '/icons/icon-192x192.png',
        badge: '/icons/icon-72x72.png',
        vibrate: [100, 50, 100],
        data: {
            dateOfArrival: Date.now(),
            primaryKey: 1
        },
        actions: [
            {
                action: 'explore',
                title: '查看进度',
                icon: '/icons/icon-72x72.png'
            },
            {
                action: '
{
  "name": "戒烟计划助手",
  "short_name": "戒烟助手",
  "description": "帮助你戒烟的健康管理应用",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#4CAF50",
  "theme_color": "#4CAF50",
  "orientation": "portrait",
  "icons": [
    {
      "src": "icons/icon-72x72.png",
      "sizes": "72x72",
      "type": "image/png"
    },
    {
      "src": "icons/icon-96x96.png",
      "sizes": "96x96",
      "type": "image/png"
    },
    {
      "src": "icons/icon-128x128.png",
      "sizes": "128x128",
      "type": "image/png"
    },
    {
      "src": "icons/icon-144x144.png",
      "sizes": "144x144",
      "type": "image/png"
    },
    {
      "src": "icons/icon-152x152.png",
      "sizes": "152x152",
      "type": "image/png"
    },
    {
      "src": "icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icons/icon-384x384.png",
      "sizes": "384x384",
      "type": "image/png"
    },
    {
      "src": "icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "categories": ["health", "lifestyle", "productivity"],
  "lang": "zh-CN",
  "dir": "ltr"
}
