# econ-teacher
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>經濟表現的量度 - 本地生產總值與本地居民總收入</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #0066cc;
            --secondary: #00a86b;
            --accent: #ff6b35;
            --warning: #ffa500;
            --error: #ff6b6b;
            --light-bg: #f5f9ff;
            --card-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #f5f9ff 0%, #e8f4f8 100%);
            min-height: 100vh;
        }

        /* 導航欄 */
        nav {
            background: linear-gradient(90deg, var(--primary) 0%, #0052a3 100%);
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            flex-wrap: wrap;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 600;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            transition: var(--transition);
            font-size: 0.95rem;
        }

        nav a:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        /* 主容器 */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* 標題頁面 */
        .hero {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            padding: 3rem 2rem;
            border-radius: 15px;
            margin-bottom: 3rem;
            text-align: center;
            box-shadow: var(--card-shadow);
        }

        .hero h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
        }

        .hero h2 {
            font-size: 1.5rem;
            margin-top: 0.5rem;
        }

        .hero p {
            font-size: 1.1rem;
            opacity: 0.95;
        }

        /* 定義框 */
        .definition-box {
            background: white;
            border-left: 5px solid var(--primary);
            padding: 2rem;
            margin: 1.5rem 0;
            border-radius: 8px;
            box-shadow: var(--card-shadow);
        }

        .definition-box h3 {
            color: var(--primary);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        .definition-box h4 {
            color: var(--primary);
            margin-bottom: 0.8rem;
            margin-top: 1rem;
        }

        .definition-box p {
            color: #555;
            line-height: 1.8;
            margin-bottom: 0.8rem;
        }

        .definition-box ol, .definition-box ul {
            margin-left: 1.5rem;
            line-height: 2;
        }

        .definition-box li {
            margin-bottom: 0.8rem;
            color: #555;
        }

        /* 公式框 */
        .formula-box {
            background: var(--light-bg);
            padding: 1.8rem;
            border-radius: 8px;
            border-left: 4px solid var(--accent);
            margin: 1.5rem 0;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
        }

        .formula-box .label {
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 1rem;
            display: block;
            font-size: 1.05rem;
        }

        .formula-box .formula {
            font-size: 1.1rem;
            line-height: 2;
            color: #333;
        }

        .formula-box .note {
            font-size: 0.95rem;
            color: #666;
            margin-top: 1rem;
            font-style: italic;
        }

        /* 解說區域 */
        .explanation-section {
            background: white;
            padding: 2.5rem;
            border-radius: 12px;
            margin-bottom: 3rem;
            box-shadow: var(--card-shadow);
        }

        .explanation-section h2 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 2rem;
            border-bottom: 3px solid var(--secondary);
            padding-bottom: 0.8rem;
        }

        .explanation-section h3 {
            color: var(--secondary);
            margin-top: 2rem;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .subsection {
            margin-bottom: 2.5rem;
            padding-bottom: 2rem;
            border-bottom: 1px solid #eee;
        }

        .subsection:last-child {
            border-bottom: none;
        }

        /* 表格樣式 */
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 1.5rem 0;
        }

        table th {
            background: var(--primary);
            color: white;
            padding: 1rem;
            text-align: left;
            font-weight: 600;
        }

        table td {
            padding: 1rem;
            border-bottom: 1px solid #ddd;
        }

        table tr:hover {
            background: var(--light-bg);
        }

        /* 要點卡片 */
        .highlight-card {
            background: #fff9e6;
            border-left: 4px solid var(--warning);
            padding: 1.5rem;
            border-radius: 8px;
            margin: 1.5rem 0;
        }

        .highlight-card h4 {
            color: var(--warning);
            margin-bottom: 0.8rem;
        }

        .highlight-card p {
            color: #555;
            line-height: 1.7;
        }

        .highlight-card ul {
            margin-left: 1.5rem;
            line-height: 1.9;
        }

        /* 包含/不包括卡片 */
        .include-exclude {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin: 2rem 0;
        }

        .include-box, .exclude-box {
            padding: 1.5rem;
            border-radius: 8px;
        }

        .include-box {
            background: #f0fdf4;
            border-left: 4px solid var(--secondary);
        }

        .exclude-box {
            background: #fff5f5;
            border-left: 4px solid var(--error);
        }

        .include-box h4, .exclude-box h4 {
            margin-bottom: 1rem;
            font-size: 1.1rem;
        }

        .include-box h4 {
            color: var(--secondary);
        }

        .exclude-box h4 {
            color: var(--error);
        }

        .include-box ul, .exclude-box ul {
            margin-left: 1.5rem;
            line-height: 1.8;
        }

        /* 術語對照表 */
        .terminology-table {
            width: 100%;
            border-collapse: collapse;
            margin: 1.5rem 0;
            background: white;
            border-radius: 8px;
            overflow: hidden;
        }

        .terminology-table th {
            background: var(--primary);
            color: white;
            padding: 1rem;
            text-align: left;
        }

        .terminology-table td {
            padding: 0.8rem 1rem;
            border-bottom: 1px solid #ddd;
        }

        /* 比較表 */
        .comparison-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin: 2rem 0;
        }

        .comparison-item {
            background: white;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--card-shadow);
        }

        .comparison-item h4 {
            color: var(--primary);
            margin-bottom: 1rem;
            font-size: 1.15rem;
        }

        .comparison-item p {
            color: #555;
            line-height: 1.7;
        }

        /* 測驗區域 */
        .quiz-section {
            background: white;
            padding: 2.5rem;
            border-radius: 12px;
            box-shadow: var(--card-shadow);
            margin-bottom: 3rem;
        }

        .quiz-section h2 {
            color: var(--primary);
            margin-bottom: 2rem;
            font-size: 2rem;
        }

        .quiz-item {
            margin-bottom: 2.5rem;
            padding-bottom: 2rem;
            border-bottom: 1px solid #eee;
        }

        .quiz-item:last-child {
            border-bottom: none;
        }

        .quiz-question {
            font-weight: 600;
            color: #333;
            margin-bottom: 1.2rem;
            font-size: 1.05rem;
        }

        .quiz-options {
            display: grid;
            gap: 0.8rem;
        }

        .option {
            padding: 1rem 1.5rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            background: white;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .option input[type="radio"] {
            cursor: pointer;
            width: 20px;
            height: 20px;
        }

        .option:hover {
            border-color: var(--primary);
            background: var(--light-bg);
        }

        .option.selected {
            border-color: var(--primary);
            background: #e3f2fd;
        }

        .option.correct {
            border-color: var(--secondary);
            background: #f0fdf4;
        }

        .option.incorrect {
            border-color: var(--error);
            background: #fff5f5;
        }

        .quiz-feedback {
            margin-top: 1rem;
            padding: 1rem;
            border-radius: 8px;
            display: none;
            font-weight: 500;
        }

        .quiz-feedback.show {
            display: block;
        }

        .quiz-feedback.correct {
            background: #f0fdf4;
            color: var(--secondary);
            border-left: 4px solid var(--secondary);
        }

        .quiz-feedback.incorrect {
            background: #fff5f5;
            color: var(--error);
            border-left: 4px solid var(--error);
        }

        /* 按鈕 */
        .btn {
            padding: 0.8rem 1.8rem;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: inline-block;
            margin-top: 1rem;
            margin-right: 0.5rem;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background: #0052a3;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0, 102, 204, 0.3);
        }

        .btn-secondary {
            background: var(--secondary);
            color: white;
        }

        .btn-secondary:hover {
            background: #008a5c;
        }

        /* Footer */
        footer {
            background: var(--primary);
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }

        /* 動畫 */
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .definition-box, .formula-box, .quiz-item {
            animation: slideIn 0.6s ease;
        }

        /* 響應式設計 */
        @media (max-width: 768px) {
            .comparison-grid, .include-exclude {
                grid-template-columns: 1fr;
            }

            .hero h1 {
                font-size: 2rem;
            }

            nav ul {
                gap: 1rem;
            }

            nav a {
                font-size: 0.9rem;
                padding: 0.4rem 0.8rem;
            }

            table {
                font-size: 0.9rem;
            }

            table th, table td {
                padding: 0.6rem;
            }
        }
    </style>
</head>
<body>
    <!-- 導航欄 -->
    <nav>
        <ul>
            <li><a href="#overview">概覽</a></li>
            <li><a href="#gdp">GDP定義</a></li>
            <li><a href="#gdp-exclude">GDP不包括</a></li>
            <li><a href="#calculation">計算方法</a></li>
            <li><a href="#gni">GNI定義</a></li>
            <li><a href="#quiz">測驗</a></li>
        </ul>
    </nav>

    <div class="container">
        <!-- 標題部分 -->
        <section class="hero" id="overview">
            <h1>📊 經濟表現的量度（I）</h1>
            <h2>本地生產總值與本地居民總收入</h2>
            <p>深入理解香港經濟的核心量度指標 | 中五經濟學課程</p>
        </section>

        <!-- ===== GDP 定義部分 ===== -->
        <section class="explanation-section" id="gdp">
            <h2>本地生產總值（GDP）</h2>

            <div class="subsection">
                <h3>1️⃣ 定義</h3>
                <div class="definition-box">
                    <p><strong>本地生產總值（GDP）</strong>是指某經濟體系的所有居民生產單位，在某指定期間內（如一季或一年）的生產總值。</p>
                </div>

                <div class="highlight-card">
                    <h4>🔑 關鍵概念：居民生產單位</h4>
                    <p>如果一個生產單位（可以是個人或機構）以某經濟體系的經濟領域為其主要的經濟利益中心，這個生產單位就是該經濟體系的居民生產單位。</p>
                    <p style="margin-top: 0.8rem;"><strong>判準：</strong>他們在某經濟體系的經濟領域內居留或打算居留至少 12 個月（就個人而言），或在該經濟體系的經濟領域內通常經營業務（就機構而言）。</p>
                </div>
            </div>

            <div class="subsection">
                <h3>💡 GDP 的核心特點</h3>
                <table>
                    <thead>
                        <tr>
                            <th>特點</th>
                            <th>說明</th>
                            <th>例子</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>地域性</td>
                            <td>按領土範圍計算</td>
                            <td>外國人在香港的生產算入香港GDP</td>
                        </tr>
                        <tr>
                            <td>時期性</td>
                            <td>通常按年或季計算</td>
                            <td>2024年香港GDP</td>
                        </tr>
                        <tr>
                            <td>增加值</td>
                            <td>只計新增價值，不重複計算</td>
                            <td>小麥→麵粉→麵包，只計增加值</td>
                        </tr>
                        <tr>
                            <td>市場價格</td>
                            <td>以當時市場價格計算</td>
                            <td>包含間接稅，扣除津貼</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- ===== GDP 不包括部分 ===== -->
        <section class="explanation-section" id="gdp-exclude">
            <h2>本地生產總值不包括的項目</h2>

            <div class="include-exclude">
                <div class="exclude-box">
                    <h4>❌ 不涉及生產的項目</h4>
                    <ul>
                        <li><strong>轉移支付</strong>（失業救濟、養老金）</li>
                        <li><strong>資本增值</strong>（股票升值）</li>
                        <li><strong>金融資產</strong>（債券買賣）</li>
                        <li><strong>二手物品</strong>（舊車轉售）</li>
                    </ul>
                </div>
                <div class="exclude-box">
                    <h4>❌ 其他不計項目</h4>
                    <ul>
                        <li><strong>進口貨品和服務</strong>（不是本地生產）</li>
                        <li><strong>過往存貨</strong>（非本期生產）</li>
                        <li><strong>無償服務</strong>（家務勞動、義工服務）</li>
                    </ul>
                </div>
            </div>

            <div class="highlight-card">
                <h4>💭 為什麼要排除這些？</h4>
                <p><strong>GDP 的目的</strong>是衡量經濟在某期間內的<strong>新增生產價值</strong>。如果計入轉移支付或二手物品，會導致重複計算，扭曲經濟表現。</p>
            </div>
        </section>

        <!-- ===== 計算方法 ===== -->
        <section class="explanation-section" id="calculation">
            <h2>GDP 的計算方法</h2>

            <!-- 生產面 -->
            <div class="subsection">
                <h3>📈 方法一：生產面 / 增加價值面</h3>
                
                <div class="definition-box">
                    <p><strong>原理：</strong>生產面透過計算在某指定期間內，全部行業所有居民生產單位的生產總值（或增加價值），以得出本地生產總值。</p>
                </div>

                <div class="formula-box">
                    <span class="label">增加價值的計算</span>
                    <div class="formula">增加價值 = 產出價值 − 中間投產消耗</div>
                    <span class="note">中間投產消耗 = 用於生產的原料、半成品等</span>
                </div>

                <div class="formula-box">
                    <span class="label">GDP 的計算</span>
                    <div class="formula">GDP = 所有居民生產單位的增加價值的總和</div>
                </div>

                <div class="comparison-grid">
                    <div class="comparison-item">
                        <h4>📌 以要素成本計算</h4>
                        <p><strong>GDP(FC) = 所有增加價值的總和</strong></p>
                        <p style="margin-top: 0.8rem; font-size: 0.95rem; color: #666;">
                            這是最純粹的生產價值，未包含政府稅收或補助的影響。
                        </p>
                    </div>
                    <div class="comparison-item">
                        <h4>📌 以市價計算</h4>
                        <p><strong>GDP(MP) = GDP(FC) + 間接稅 − 津貼</strong></p>
                        <p style="margin-top: 0.8rem; font-size: 0.95rem; color: #666;">
                            這是消費者實際支付的價格，包含政府的稅收和補助。
                        </p>
                    </div>
                </div>

                <div class="highlight-card">
                    <h4>📚 實例：麵包的生產增加值</h4>
                    <ul style="margin-left: 1.5rem; margin-top: 1rem;">
                        <li><strong>農民生產小麥：</strong>市場價值 $100</li>
                        <li><strong>麵粉廠：</strong>購買小麥 $100，加工成麵粉售 $200
                            <ul style="margin-left: 2rem; margin-top: 0.5rem;">
                                <li>增加值 = $200 − $100 = <strong style="color: var(--secondary);">$100</strong></li>
                            </ul>
                        </li>
                        <li><strong>麵包店：</strong>購買麵粉 $200，製成麵包售 $400
                            <ul style="margin-left: 2rem; margin-top: 0.5rem;">
                                <li>增加值 = $400 − $200 = <strong style="color: var(--secondary);">$200</strong></li>
                            </ul>
                        </li>
                        <li style="margin-top: 1rem; border-top: 2px solid #ffa500; padding-top: 1rem; color: var(--secondary); font-weight: bold;">
                            ✓ 生產面 GDP = $100 + $100 + $200 = <strong>$400</strong>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- 開支面 -->
            <div class="subsection">
                <h3>💰 方法二：開支面 / 支出法</h3>

                <div class="definition-box">
                    <p><strong>原理：</strong>GDP 等於所有最終商品和服務的支出總和。這反映了整個經濟的總需求。</p>
                </div>

                <div class="formula-box">
                    <span class="label">開支面公式</span>
                    <div class="formula">GDP(MP) = C + I + G + (X − M)</div>
                </div>

                <div style="background: white; padding: 1.5rem; border-radius: 8px; margin: 1.5rem 0; border: 2px solid var(--primary);">
                    <h4 style="color: var(--primary); margin-bottom: 1rem;">📖 各項組成說明</h4>
                    <table class="terminology-table">
                        <thead>
                            <tr>
                                <th style="width: 15%;">代號</th>
                                <th style="width: 35%;">項目</th>
                                <th style="width: 50%;">詳細說明</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>C</strong></td>
                                <td>私人消費開支</td>
                                <td>家庭購買商品和服務的支出（食物、衣服、醫療等）</td>
                            </tr>
                            <tr>
                                <td><strong>I</strong></td>
                                <td>投資總額</td>
                                <td>企業購置設備、建廠、存貨增減等<br>
                                    <em>I = 固定投資 + 存貨增減 = 折舊 + 投資淨額</em></td>
                            </tr>
                            <tr>
                                <td><strong>G</strong></td>
                                <td>政府消費開支</td>
                                <td>政府購買商品和服務（公務員薪水、基建、教育）</td>
                            </tr>
                            <tr>
                                <td><strong>X</strong></td>
                                <td>出口總值</td>
                                <td>貨品出口 + 服務輸出<br>
                                    = (本地貨品出口 + 貨品轉口) + 服務輸出</td>
                            </tr>
                            <tr>
                                <td><strong>M</strong></td>
                                <td>進口總值</td>
                                <td>貨品進口 + 服務輸入</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <div class="highlight-card">
                    <h4>📌 投資組成的詳細公式</h4>
                    <p style="margin-top: 0.8rem;">投資總額可以用多種方式表達：</p>
                    <ul style="margin-left: 1.5rem; margin-top: 1rem;">
                        <li><strong>方式1：</strong> I = 固定投資 + 存貨增減</li>
                        <li><strong>方式2：</strong> I = (折舊 + 固定投資淨額) + 存貨增減</li>
                        <li><strong>方式3：</strong> I = 折舊 + 投資淨額</li>
                    </ul>
                </div>

                <div class="highlight-card">
                    <h4>📚 開支面 GDP 實例</h4>
                    <p style="margin-top: 0.8rem;">假設某年的數據：</p>
                    <table style="margin-left: 1.5rem; margin-top: 1rem; border: none;">
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">C （私人消費） </td>
                            <td style="border: none; padding: 0.4rem 0;"> = $3,500 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">I （投資）</td>
                            <td style="border: none; padding: 0.4rem 0;"> = $1,200 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">G （政府支出）</td>
                            <td style="border: none; padding: 0.4rem 0;"> = $900 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">X （出口）</td>
                            <td style="border: none; padding: 0.4rem 0;"> = $2,800 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">M （進口）</td>
                            <td style="border: none; padding: 0.4rem 0;"> = $2,600 億</td>
                        </tr>
                        <tr style="border-top: 2px solid #999; border-bottom: none; border-left: none; border-right: none;">
                            <td style="border: none; padding: 0.8rem 0; font-weight: bold;">GDP</td>
                            <td style="border: none; padding: 0.8rem 0; color: var(--secondary); font-weight: bold;"> = 3500 + 1200 + 900 + (2800 − 2600) = <strong>$5,800 億</strong></td>
                        </tr>
                    </table>
                </div>

                <div class="definition-box">
                    <h4>📖 術語對照（別稱）</h4>
                    <table class="terminology-table">
                        <thead>
                            <tr>
                                <th>標準名稱</th>
                                <th>別稱 / 簡稱</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>投資總額</td>
                                <td>本地資本形成總額（GFCF）</td>
                            </tr>
                            <tr>
                                <td>固定投資總額</td>
                                <td>本地固定資本形成總額</td>
                            </tr>
                            <tr>
                                <td>固定投資淨額</td>
                                <td>本地固定資本形成淨額</td>
                            </tr>
                            <tr>
                                <td>折舊</td>
                                <td>資本消耗免稅額（CCA）</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- 收入面 -->
            <div class="subsection">
                <h3>💵 方法三：收入面</h3>

                <div class="definition-box">
                    <p><strong>原理：</strong>GDP 等於所有要素收入的總和。從收入角度看，生產中的每一分錢都成為某人的收入（工資、利息、租金或利潤）。</p>
                </div>

                <div class="formula-box">
                    <span class="label">收入面公式</span>
                    <div class="formula">GDP = 工資 + 利息 + 租金 + 利潤</div>
                </div>

                <div style="background: white; padding: 1.5rem; border-radius: 8px; margin: 1.5rem 0; border: 2px solid var(--primary);">
                    <h4 style="color: var(--primary); margin-bottom: 1rem;">📖 各項收入來源說明</h4>
                    <table class="terminology-table">
                        <thead>
                            <tr>
                                <th>收入類型</th>
                                <th>來源</th>
                                <th>例子</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>工資</strong></td>
                                <td>勞動報酬</td>
                                <td>員工薪水、公務員薪酬</td>
                            </tr>
                            <tr>
                                <td><strong>利息</strong></td>
                                <td>資本報酬</td>
                                <td>銀行利息、債券收入</td>
                            </tr>
                            <tr>
                                <td><strong>租金</strong></td>
                                <td>土地報酬</td>
                                <td>房租、地租收入</td>
                            </tr>
                            <tr>
                                <td><strong>利潤</strong></td>
                                <td>企業家報酬</td>
                                <td>商業利潤、股息</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <div class="highlight-card">
                    <h4>📚 收入面 GDP 實例</h4>
                    <p style="margin-top: 0.8rem;">假設某年的收入統計：</p>
                    <table style="margin-left: 1.5rem; margin-top: 1rem; border: none;">
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">工資（僱員薪金）</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $3,200 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">利息（資本收入）</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $800 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">租金（物業收入）</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $900 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">利潤（企業盈利）</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $900 億</td>
                        </tr>
                        <tr style="border-top: 2px solid #999; border-bottom: none; border-left: none; border-right: none;">
                            <td style="border: none; padding: 0.8rem 0; font-weight: bold;">GDP</td>
                            <td style="border: none; padding: 0.8rem 0; text-align: right; color: var(--secondary); font-weight: bold;"> = <strong>$5,800 億</strong></td>
                        </tr>
                    </table>
                </div>
            </div>

            <div class="highlight-card">
                <h4>✨ 三種方法的一致性</h4>
                <p style="margin-top: 0.8rem;">在同一經濟體系中，三種計算方法得出的 GDP 數值應該相同：</p>
                <p style="margin-top: 1rem; text-align: center; font-weight: bold; color: var(--primary);">
                    生產面 GDP = 開支面 GDP = 收入面 GDP
                </p>
                <p style="margin-top: 1rem; color: #666;">這是因為：生產的產值 = 支出的總額 = 所有參與者的收入總和</p>
            </div>
        </section>

        <!-- ===== GNI 定義部分 ===== -->
        <section class="explanation-section" id="gni">
            <h2>本地居民總收入（GNI）</h2>

            <div class="subsection">
                <h3>1️⃣ 定義</h3>
                <div class="definition-box">
                    <p><strong>本地居民總收入（GNI）</strong>是指一個經濟體系的居民，在某指定期間內，透過從事各項經濟活動而賺取的總收入。</p>
                </div>

                <div class="highlight-card">
                    <h4>🔑 關鍵概念：經濟體系的居民</h4>
                    <ul style="margin-left: 1.5rem; margin-top: 1rem;">
                        <li><strong>個人：</strong>如果某人在某經濟體系內居留或打算居留至少 12 個月，他在國民收入統計上便屬於該經濟體系的居民，<strong>不論他屬於甚麼國籍</strong>。</li>
                        <li><strong>機構：</strong>如果某機構在某經濟體系內通常經營業務，它在國民收入統計上便屬於該經濟體系的居民。</li>
                    </ul>
                </div>
            </div>

            <div class="subsection">
                <h3>2️⃣ GNI 與 GDP 的關係</h3>

                <div class="formula-box">
                    <span class="label">GNI 的計算公式</span>
                    <div class="formula">GNI = GDP + (從外地賺取的要素收入 − 支付給外地的要素收入)</div>
                    <div class="formula" style="margin-top: 1rem;">或</div>
                    <div class="formula" style="margin-top: 1rem;">GNI = GDP + 從外地所賺取的淨要素收入</div>
                </div>

                <div class="comparison-grid">
                    <div class="comparison-item">
                        <h4>📍 GDP 的特點</h4>
                        <ul style="margin-left: 1.5rem; margin-top: 0.8rem;">
                            <li><strong>地域概念：</strong>按領土範圍</li>
                            <li><strong>包含：</strong>外國人在本地的收入</li>
                            <li><strong>不包含：</strong>本地人在海外的收入</li>
                        </ul>
                    </div>
                    <div class="comparison-item">
                        <h4>👥 GNI 的特點</h4>
                        <ul style="margin-left: 1.5rem; margin-top: 0.8rem;">
                            <li><strong>居民概念：</strong>按國民身份</li>
                            <li><strong>包含：</strong>本地人在海外的收入</li>
                            <li><strong>不包含：</strong>外國人在本地的收入</li>
                        </ul>
                    </div>
                </div>

                <div class="highlight-card">
                    <h4>📚 GDP 與 GNI 的具體例子</h4>
                    <p style="margin-top: 0.8rem;"><strong>情境：</strong>某年香港的經濟統計</p>
                    <table style="margin-left: 1.5rem; margin-top: 1rem; border: none;">
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">香港 GDP</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $5,800 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">加：香港人在海外的要素收入</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $200 億</td>
                        </tr>
                        <tr style="border: none;">
                            <td style="border: none; padding: 0.4rem 0;">減：外國人在香港的要素收入</td>
                            <td style="border: none; padding: 0.4rem 0; text-align: right;"> = $150 億</td>
                        </tr>
                        <tr style="border-top: 2px solid #999; border-bottom: none; border-left: none; border-right: none;">
                            <td style="border: none; padding: 0.8rem 0; font-weight: bold;">GNI</td>
                            <td style="border: none; padding: 0.8rem 0; text-align: right; color: var(--secondary); font-weight: bold;"> = 5800 + 200 − 150 = <strong>$5,850 億</strong></td>
                        </tr>
                    </table>
                </div>
            </div>

            <div class="subsection">
                <h3>3️⃣ GDP 與 GNI 的差異詳解</h3>

                <table>
                    <thead>
                        <tr>
                            <th>比較項目</th>
                            <th>GDP</th>
                            <th>GNI</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>概念基礎</strong></td>
                            <td>地域（領土）</td>
                            <td>居民（身份）</td>
                        </tr>
                        <tr>
                            <td><strong>計算對象</strong></td>
                            <td>在某領土內生產的價值</td>
                            <td>該國居民賺取的收入</td>
                        </tr>
                        <tr>
                            <td><strong>包含外國人</strong></td>
                            <td>✓ 包含在本地的收入</td>
                            <td>✗ 不包含外國人收入</td>
                        </tr>
                        <tr>
                            <td><strong>包含本地人海外收入</strong></td>
                            <td>✗ 不包含</td>
                            <td>✓ 包含</td>
                        </tr>
                        <tr>
                            <td><strong>適用場景</strong></td>
                            <td>衡量經濟生產力、規模</td>
                            <td>衡量居民福祉、實際收入</td>
                        </tr>
                    </tbody>
                </table>

                <div class="highlight-card">
                    <h4>💡 香港的特殊情況</h4>
                    <p style="margin-top: 0.8rem;">香港是國際金融中心，外資進出頻繁。因此：</p>
                    <ul style="margin-left: 1.5rem; margin-top: 1rem;">
                        <li>很多外國人在香港工作，他們的收入算入 GDP</li>
                        <li>很多香港人在海外工作或投資，他們的收入算入 GNI</li>
                        <li>結果：<strong>香港的 GNI 可能小於或大於 GDP</strong></li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- ===== 測驗部分 ===== -->
        <section class="quiz-section" id="quiz">
            <h2>🎯 即時訓練：檢查你的理解</h2>
            
            <div class="quiz-item">
                <div class="quiz-question">
                    問題 1：下列哪一項應計入香港的 GDP？
                </div>
                <form class="quiz-options" onchange="checkAnswer(this, 'q1')">
                    <label class="option">
                        <input type="radio" name="q1" value="a">
                        <span>A) 香港人在英國倫敦工作賺取的薪水</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="b">
                        <span>B) 一部已使用3年的二手手機的轉售</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="c" data-correct="true">
                        <span>C) ✓ 美國人在香港購買房地產的價值</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q1" value="d">
                        <span>D) 政府向失業者發放的失業救濟金</span>
                    </label>
                </form>
                <div class="quiz-feedback" id="feedback-q1"></div>
            </div>

            <div class="quiz-item">
                <div class="quiz-question">
                    問題 2：若農民生產小麥賣 $100，麵粉廠用 $100 小麥製麵粉賣 $200，
                    麵包店用 $200 麵粉製麵包賣 $400。使用生產面方法計算 GDP 時應為：
                </div>
                <form class="quiz-options" onchange="checkAnswer(this, 'q2')">
                    <label class="option">
                        <input type="radio" name="q2" value="a">
                        <span>A) $100 + $200 + $400 = $700（會重複計算）</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="b" data-correct="true">
                        <span>B) ✓ $100 + $100 + $200 = $400（增加值法）</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="c">
                        <span>C) 只計 $400（最終產品價格）</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q2" value="d">
                        <span>D) 無法確定</span>
                    </label>
                </form>
                <div class="quiz-feedback" id="feedback-q2"></div>
            </div>

            <div class="quiz-item">
                <div class="quiz-question">
                    問題 3：以開支面計算 GDP，公式為 GDP = C + I + G + (X − M)。
                    下列哪個選項對 C 的定義最準確？
                </div>
                <form class="quiz-options" onchange="checkAnswer(this, 'q3')">
                    <label class="option">
                        <input type="radio" name="q3" value="a">
                        <span>A) 企業的資本投資</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="b" data-correct="true">
                        <span>B) ✓ 家庭購買商品和服務的支出</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="c">
                        <span>C) 政府支出</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q3" value="d">
                        <span>D) 國民在海外的消費</span>
                    </label>
                </form>
                <div class="quiz-feedback" id="feedback-q3"></div>
            </div>

            <div class="quiz-item">
                <div class="quiz-question">
                    問題 4：GNI 與 GDP 的主要差異在於：
                </div>
                <form class="quiz-options" onchange="checkAnswer(this, 'q4')">
                    <label class="option">
                        <input type="radio" name="q4" value="a">
                        <span>A) GNI 總是比 GDP 大</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="b" data-correct="true">
                        <span>B) ✓ GDP 按地域，GNI 按居民身份；加上淨要素收入調整</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="c">
                        <span>C) GNI 只包括貨品，不包括服務</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q4" value="d">
                        <span>D) GNI 和 GDP 完全相同，只是名稱不同</span>
                    </label>
                </form>
                <div class="quiz-feedback" id="feedback-q4"></div>
            </div>

            <div class="quiz-item">
                <div class="quiz-question">
                    問題 5：某居民在新加坡投資公司獲得的利息收入 $50 萬。
                    下列敘述何者正確？
                </div>
                <form class="quiz-options" onchange="checkAnswer(this, 'q5')">
                    <label class="option">
                        <input type="radio" name="q5" value="a">
                        <span>A) 計入香港 GDP 和 GNI</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="b" data-correct="true">
                        <span>B) ✓ 計入香港 GNI，但不計入香港 GDP</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="c">
                        <span>C) 計入香港 GDP，但不計入香港 GNI</span>
                    </label>
                    <label class="option">
                        <input type="radio" name="q5" value="d">
                        <span>D) 既不計入 GDP 也不計入 GNI</span>
                    </label>
                </form>
                <div class="quiz-feedback" id="feedback-q5"></div>
            </div>

            <button class="btn btn-primary" onclick="resetQuiz()">🔄 重新開始</button>
            <button class="btn btn-secondary" onclick="showScores()">📊 查看成績</button>
        </section>

        <!-- 重點總結 -->
        <section class="explanation-section" style="background: linear-gradient(135deg, rgba(0, 102, 204, 0.05) 0%, rgba(0, 168, 107, 0.05) 100%);">
            <h2>📋 重點總結</h2>

            <div class="subsection">
                <h3>GDP 的核心公式</h3>
                <div class="formula-box">
                    <span class="label">1. 生產面</span>
                    <div class="formula">GDP = Σ(產出價值 − 中間投產消耗) = Σ增加價值</div>
                </div>
                <div class="formula-box">
                    <span class="label">2. 開支面</span>
                    <div class="formula">GDP = C + I + G + (X − M)</div>
                </div>
                <div class="formula-box">
                    <span class="label">3. 收入面</span>
                    <div class="formula">GDP = 工資 + 利息 + 租金 + 利潤</div>
                </div>
                <div class="formula-box">
                    <span class="label">4. 市價與要素成本</span>
                    <div class="formula">GDP(MP) = GDP(FC) + 間接稅 − 津貼</div>
                </div>
            </div>

            <div class="subsection">
                <h3>GDP 與 GNI 的關係</h3>
                <div class="formula-box">
                    <span class="label">計算公式</span>
                    <div class="formula">GNI = GDP + 淨要素收入</div>
                    <div class="formula" style="margin-top: 1rem;">淨要素收入 = 從外地賺取的要素收入 − 支付給外地的要素收入</div>
                </div>
            </div>

            <div class="subsection">
                <h3>常見易混淆點</h3>
                <table>
                    <thead>
                        <tr>
                            <th>易混淆項目</th>
                            <th>區別</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>GDP vs GNI</strong></td>
                            <td>GDP 按地域（在香港生產的），GNI 按居民（香港人的收入）</td>
                        </tr>
                        <tr>
                            <td><strong>增加值 vs 產出</strong></td>
                            <td>增加值 = 產出 − 中間投入，避免重複計算</td>
                        </tr>
                        <tr>
                            <td><strong>市價 vs 要素成本</strong></td>
                            <td>市價包含稅收和補助，要素成本是純生產成本</td>
                        </tr>
                        <tr>
                            <td><strong>消費支出 vs 投資</strong></td>
                            <td>消費是使用，投資是形成資本（設備、廠房）</td>
                        </tr>
                        <tr>
                            <td><strong>轉移支付</strong></td>
                            <td>轉移支付不計入 GDP，因為不是新生產</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer>
        <p>© 2026 香港中學經濟學教學平台 | 中五經濟學課程輔助材料</p>
        <p>第 1 課：經濟表現的量度（I）── 本地生產總值與本地居民總收入</p>
    </footer>

    <script>
        // 追蹤答案
        let scores = {
            correct: 0,
            total: 5
        };

        function checkAnswer(form, questionId) {
            const selectedOption = form.querySelector('input[type="radio"]:checked');
            if (!selectedOption) return;

            // 清除之前的樣式
            form.querySelectorAll('.option').forEach(opt => {
                opt.classList.remove('selected', 'correct', 'incorrect');
            });

            // 找到被選中的選項容器
            const selectedLabel = selectedOption.closest('label');
            selectedLabel.classList.add('selected');

            // 檢查是否正確
            const isCorrect = selectedOption.hasAttribute('data-correct');
            const feedback = document.getElementById(`feedback-${questionId}`);

            if (isCorrect) {
                selectedLabel.classList.add('correct');
                feedback.textContent = '✅ 正確！很好的理解。';
                feedback.classList.add('correct', 'show');
                if (!selectedOption.dataset.scored) {
                    scores.correct++;
                    selectedOption.dataset.scored = 'true';
                }
            } else {
                selectedLabel.classList.add('incorrect');
                // 找到正確答案
                const correctOption = form.querySelector('input[data-correct]');
                const correctLabel = correctOption.closest('label');
                correctLabel.classList.add('correct');
                
                feedback.textContent = '❌ 這不是正確答案。請再看一遍上面的解說。';
                feedback.classList.add('incorrect', 'show');
            }
        }

        function resetQuiz() {
            // 重置所有選項
            document.querySelectorAll('input[type="radio"]').forEach(input => {
                input.checked = false;
                input.dataset.scored = '';
            });

            // 清除所有反饋
            document.querySelectorAll('.quiz-feedback').forEach(feedback => {
                feedback.classList.remove('show');
            });

            // 清除樣式
            document.querySelectorAll('.option').forEach(opt => {
                opt.classList.remove('selected', 'correct', 'incorrect');
            });

            // 重置分數
            scores = { correct: 0, total: 5 };
            alert('已重新開始！');
        }

        function showScores() {
            const percentage = (scores.correct / scores.total) * 100;
            let feedback = '';
            
            if (percentage === 100) {
                feedback = '🏆 太棒了！你完全掌握了 GDP 和 GNI 的核心概念！';
            } else if (percentage >= 80) {
                feedback = '👍 很不錯！你已經理解了大部分內容，再溫習一下易混淆的部分。';
            } else if (percentage >= 60) {
                feedback = '📚 有進步！建議再讀一遍詳細解說部分。';
            } else {
                feedback = '💪 繼續加油！建議從基本概念開始重新學習。';
            }

            alert(`你的成績：${scores.correct}/${scores.total} (${percentage.toFixed(0)}%)\n\n${feedback}`);
        }

        // 平滑滾動
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                target.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>
