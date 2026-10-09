<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ココロ充電おみくじ 〜今日のあなたにそっと寄り添う言葉〜</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Zen+Maru+Gothic:wght@400;500;700;900&family=Shippori+Mincho:wght@600;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-color: #0d081a;
            --card-bg: rgba(28, 20, 50, 0.85);
            --card-border: #4a3a70;
            --accent-gold: #ffd700;
            --accent-gold-glow: rgba(255, 215, 0, 0.4);
            --text-main: #f0eafc;
            --text-sub: #b8a8db;
            --btn-purple: linear-gradient(135deg, #7b2cbf 0%, #9d4edd 50%, #e0aaff 100%);
            --btn-hover: linear-gradient(135deg, #9d4edd 0%, #c77dff 50%, #e0aaff 100%);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: radial-gradient(circle at center, #1b1233 0%, #0d081a 100%);
            color: var(--text-main);
            font-family: 'Zen Maru Gothic', sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px 15px;
            position: relative;
            overflow-x: hidden;
        }

        /* 背景の星模様 */
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            background: radial-gradient(2px 2px at 20px 30px, #ffffff, rgba(0,0,0,0)),
                        radial-gradient(2px 2px at 40px 70px, #ffd700, rgba(0,0,0,0)),
                        radial-gradient(1px 1px at 90px 40px, #ffffff, rgba(0,0,0,0)),
                        radial-gradient(2px 2px at 160px 120px, #dda0dd, rgba(0,0,0,0));
            background-repeat: repeat;
            background-size: 200px 200px;
            opacity: 0.5;
            z-index: 0;
        }

        .container {
            width: 100%;
            max-width: 760px;
            z-index: 1;
        }

        header {
            text-align: center;
            margin-bottom: 25px;
        }

        .sub-subtitle {
            font-size: clamp(1rem, 2.5vw, 1.25rem);
            color: var(--accent-gold);
            letter-spacing: 3px;
            font-weight: 700;
            margin-bottom: 8px;
        }

        h1 {
            font-family: 'Shippori Mincho', serif;
            font-size: clamp(2.2rem, 5vw, 3.2rem);
            color: #fff;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.6);
            margin-bottom: 8px;
            letter-spacing: 2px;
        }

        .subtitle {
            font-size: clamp(1.1rem, 2.8vw, 1.4rem);
            color: var(--text-sub);
        }

        .main-card {
            background: var(--card-bg);
            border: 2px solid var(--accent-gold);
            box-shadow: 0 0 25px rgba(123, 44, 191, 0.4), inset 0 0 15px rgba(255, 215, 0, 0.1);
            border-radius: 24px;
            padding: clamp(20px, 4vw, 35px);
            backdrop-filter: blur(10px);
        }

        .section-title {
            font-size: clamp(1.2rem, 3.2vw, 1.5rem);
            color: var(--accent-gold);
            margin-bottom: 12px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* 選択グリッド（立場 4項目対応） */
        .grid-options-4 {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            margin-bottom: 25px;
        }

        .grid-options-3 {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin-bottom: 25px;
        }

        @media (max-width: 600px) {
            .grid-options-4 {
                grid-template-columns: repeat(2, 1fr);
            }
            .grid-options-3 {
                grid-template-columns: 1fr;
            }
        }

        .option-card {
            background: rgba(15, 10, 30, 0.6);
            border: 2px solid #3d2c5e;
            border-radius: 16px;
            padding: 14px 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.25s ease;
            user-select: none;
        }

        .option-card:hover {
            border-color: #8a53d4;
            transform: translateY(-2px);
        }

        .option-card.selected {
            border-color: var(--accent-gold);
            background: rgba(123, 44, 191, 0.35);
            box-shadow: 0 0 15px var(--accent-gold-glow);
        }

        .option-icon {
            font-size: clamp(1.8rem, 3.5vw, 2.5rem);
            margin-bottom: 4px;
            display: block;
        }

        .option-label {
            font-size: clamp(1.05rem, 2.6vw, 1.3rem);
            font-weight: 700;
            color: #fff;
        }

        .option-desc {
            font-size: clamp(0.85rem, 2vw, 1rem);
            color: var(--text-sub);
            margin-top: 3px;
        }

        /* プルダウンのスタイル */
        .select-wrapper {
            margin-bottom: 28px;
        }

        .custom-select {
            width: 100%;
            padding: 14px 18px;
            background: rgba(15, 10, 30, 0.8);
            border: 2px solid #3d2c5e;
            border-radius: 14px;
            color: #ffffff;
            font-family: 'Zen Maru Gothic', sans-serif;
            font-size: clamp(1.05rem, 2.8vw, 1.3rem);
            font-weight: 700;
            cursor: pointer;
            outline: none;
            transition: all 0.25s ease;
            appearance: none;
            background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23ffd700'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");
            background-repeat: no-repeat;
            background-position: right 16px center;
            background-size: 24px;
        }

        .custom-select:focus, .custom-select:hover {
            border-color: var(--accent-gold);
            box-shadow: 0 0 12px rgba(255, 215, 0, 0.2);
        }

        .custom-select option {
            background-color: #170d2c;
            color: #ffffff;
            padding: 10px;
        }

        /* 占うボタン */
        .btn-submit {
            width: 100%;
            padding: 18px 20px;
            border: 2px solid var(--accent-gold);
            border-radius: 50px;
            background: var(--btn-purple);
            color: #fff;
            font-size: clamp(1.4rem, 3.8vw, 1.8rem);
            font-weight: 900;
            letter-spacing: 4px;
            cursor: pointer;
            box-shadow: 0 6px 20px rgba(123, 44, 191, 0.6), 0 0 15px var(--accent-gold-glow);
            transition: all 0.3s ease;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }

        .btn-submit:hover {
            background: var(--btn-hover);
            transform: scale(1.02);
            box-shadow: 0 8px 25px rgba(157, 78, 221, 0.8), 0 0 25px var(--accent-gold);
        }

        .btn-submit:active {
            transform: scale(0.98);
        }

        /* 結果エリア */
        .result-container {
            display: none;
            margin-top: 30px;
            animation: fadeIn 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .result-card {
            background: rgba(20, 14, 40, 0.95);
            border: 2px solid var(--accent-gold);
            border-radius: 20px;
            padding: clamp(20px, 4vw, 30px);
            margin-bottom: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* 項目間で統一されたスタイル */
        .result-header {
            font-size: clamp(1.3rem, 3.5vw, 1.6rem);
            color: var(--accent-gold);
            border-bottom: 2px dashed #4a3a70;
            padding-bottom: 10px;
            margin-bottom: 15px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .result-body {
            font-size: clamp(1.15rem, 3vw, 1.35rem);
            line-height: 1.8;
            color: #ffffff;
            text-align: left;
        }

        .btn-reset {
            background: transparent;
            border: 1px solid var(--text-sub);
            color: var(--text-sub);
            padding: 12px 25px;
            border-radius: 30px;
            font-size: clamp(1rem, 2.5vw, 1.2rem);
            cursor: pointer;
            display: block;
            margin: 20px auto 0;
            transition: all 0.2s ease;
        }

        .btn-reset:hover {
            color: #fff;
            border-color: #fff;
            background: rgba(255,255,255,0.1);
        }
    </style>
</head>
<body>
    <div class="stars"></div>

    <div class="container">
        <header>
            <div class="sub-subtitle">✦ HEART RECHARGE ORACLE ✦</div>
            <h1>ココロ充電おみくじ</h1>
            <div class="subtitle">〜 今日のあなたにそっと寄り添う言葉 〜</div>
        </header>

        <div class="main-card">
            <!-- STEP 1: 職業 / 立場 -->
            <div class="section-title">✦ 1. あなたの「現在の立場」を選択</div>
            <div class="grid-options-4" id="job-options">
                <div class="option-card selected" data-value="unselected">
                    <span class="option-icon">🌟</span>
                    <div class="option-label">指定なし</div>
                    <div class="option-desc">誰でもOK</div>
                </div>
                <div class="option-card" data-value="student">
                    <span class="option-icon">🎓</span>
                    <div class="option-label">学生</div>
                    <div class="option-desc">学業・部活</div>
                </div>
                <div class="option-card" data-value="worker">
                    <span class="option-icon">💼</span>
                    <div class="option-label">社会人</div>
                    <div class="option-desc">仕事・人間関係</div>
                </div>
                <div class="option-card" data-value="seeker">
                    <span class="option-icon">🌱</span>
                    <div class="option-label">求職中</div>
                    <div class="option-desc">就活・未来探し</div>
                </div>
            </div>

            <!-- STEP 2: 星座選択（プルダウン） -->
            <div class="section-title">✦ 2. あなたの「星座」を選択（任意）</div>
            <div class="select-wrapper">
                <select id="zodiac-select" class="custom-select">
                    <option value="none">✨ 選択なし（星の共通メッセージ）</option>
                    <option value="aries">♈ 牡羊座（3/21 〜 4/19）</option>
                    <option value="taurus">♉ 牡牛座（4/20 〜 5/20）</option>
                    <option value="gemini">♊ 双子座（5/21 〜 6/21）</option>
                    <option value="cancer">♋ 蟹座（6/22 〜 7/22）</option>
                    <option value="leo">♌ 獅子座（7/23 〜 8/22）</option>
                    <option value="virgo">♍ 乙女座（8/23 〜 9/22）</option>
                    <option value="libra">♎ 天秤座（9/23 〜 10/23）</option>
                    <option value="scorpio">♏ 蠍座（10/24 〜 11/22）</option>
                    <option value="sagittarius">♐ 射手座（11/23 〜 12/21）</option>
                    <option value="capricorn">♑ 山羊座（12/22 〜 1/19）</option>
                    <option value="aquarius">♒ 水瓶座（1/20 〜 2/18）</option>
                    <option value="pisces">♓ 魚座（2/19 〜 3/20）</option>
                </select>
            </div>

            <!-- STEP 3: HP -->
            <div class="section-title">✦ 3. 今日の「心と体のHP（パワー）」は？</div>
            <div class="grid-options-3" id="hp-options">
                <div class="option-card selected" data-value="100">
                    <span class="option-icon">⚡️</span>
                    <div class="option-label" style="color: #4ade80;">100%</div>
                    <div class="option-desc">絶好調！</div>
                </div>
                <div class="option-card" data-value="50">
                    <span class="option-icon">🔋</span>
                    <div class="option-label" style="color: #facc15;">50%</div>
                    <div class="option-desc">ぼちぼち</div>
                </div>
                <div class="option-card" data-value="10">
                    <span class="option-icon">🪫</span>
                    <div class="option-label" style="color: #f87171;">10%</div>
                    <div class="option-desc">限界寸前</div>
                </div>
            </div>

            <!-- 占うボタン -->
            <button class="btn-submit" id="btn-fortune">
                <span>✨ 占 う ✨</span>
            </button>
        </div>

        <!-- 結果表示エリア -->
        <div class="result-container" id="result-area">
            <!-- 1. 運勢 -->
            <div class="result-card">
                <div class="result-header">🔮 今日の運勢メッセージ</div>
                <div class="result-body" id="res-fortune"></div>
            </div>

            <!-- 2. 星座のアドバイス -->
            <div class="result-card">
                <div class="result-header">⭐ 星座のワンポイントアドバイス</div>
                <div class="result-body" id="res-zodiac"></div>
            </div>

            <!-- 3. ラッキーアイテム -->
            <div class="result-card">
                <div class="result-header">🎁 身近なラッキーアイテム</div>
                <div class="result-body" id="res-item"></div>
            </div>

            <!-- 4. HP回復呪文 -->
            <div class="result-card">
                <div class="result-header">💖 HP回復の呪文（今日の労い言葉）</div>
                <div class="result-body" id="res-spell"></div>
            </div>

            <!-- 5. プチクエスト -->
            <div class="result-card">
                <div class="result-header">🎯 今日のプチクエスト</div>
                <div class="result-body" id="res-quest"></div>
            </div>

            <button class="btn-reset" id="btn-reset">もう一度占う</button>
        </div>
    </div>

    <script>
        // 状態保持
        let selectedJob = 'unselected';
        let selectedHp = '100';

        // 占いデータベース（立場 x HP）
        const fortuneData = {
            unselected: {
                '100': [
                    "今日のあなたはエネルギー満タン！好奇心の向くままに行動すると予想以上の素晴らしい発見や幸運に出会える一日です。",
                    "素晴らしいバイタリティが湧き出ています。気になっていたことや新しい体験に足を踏み入れるのに最高のタイミング！"
                ],
                '50': [
                    "マイペースで過ごすことで自然と運気が整う好日。無理にスケジュールを詰め込まず、ゆとりを楽しむ時間を大切に。",
                    "穏やかな良い波に乗っています。自分の好きなお茶を楽しんだり、静かな時間を大切にすると心がふんわり癒やされます。"
                ],
                '10': [
                    "今日はとにかく自分を甘やかして休ませる日。今日一日を無事に過ごしているだけで、あなたはもう100点満点です！",
                    "心も体も省エネ運転でOK。好きな動画を見たり、早めにお布団に入って頑張った自分をハグしてあげましょう。"
                ]
            },
            student: {
                '100': [
                    "今日のあなたは集中力とひらめきが最高潮！学びや新しい挑戦が面白いほど身につく大吉日です。部活やサークルでもキーマンとして大活躍できそう。",
                    "素晴らしいポジティブなエネルギーに満ちています！今まで苦手だった分野に手をつけると、あっさり克服できるチャンスです。"
                ],
                '50': [
                    "マイペースに進めることで着実に成果が出る穏やかな一日。焦らず自分のリズムを守れば、周囲とも心地よい関係を保てます。",
                    "授業や課題は「できた分」を自分を褒めてあげましょう。放課後は好きな音楽を聞いてリラックスするのが吉。"
                ],
                '10': [
                    "今日はとにかく「休むこと」が最大の勉強です！限界まで頑張った自分にハナマルをあげて、今日は最低限の課題だけ終わらせて早く寝ましょう。",
                    "心も体も省エネモードでOK。誰かと比べず、あたたかい飲み物を飲んで自分を一番に甘やかしてください。"
                ]
            },
            worker: {
                '100': [
                    "圧倒的な決断力と推進力がある一日！溜まっていたタスクを一気に片付けたり、新しい提案をするのに絶好のタイミングです。",
                    "周りへの配慮とリーダーシップが光ります。あなたの前向きな姿勢がチーム全体の雰囲気を明るく引き上げます！"
                ],
                '50': [
                    "堅実でブレない対応ができる安定運です。いつも通りの丁寧な仕事をこなすことで、周囲からの信頼がさらに深まります。",
                    "定時退社や早めの帰宅を意識すると満足度がアップ。効率良くタスクを区切って、夜は自分の時間を楽しみましょう。"
                ],
                '10': [
                    "今日生きているだけで100点満点です！仕事の精度は「6割できれば大成功」と割り切って、無理な依頼は優しく断りましょう。",
                    "あなたはすでに十分すぎるほど頑張っています。今日は定時で帰り、お風呂にゆっくり浸かって自分を労わってください。"
                ]
            },
            seeker: {
                '100': [
                    "あなたの魅力やこれまでの努力がしっかりと実を結ぶ前兆です！新しい求人や情報との素晴らしい出会いがある予感。",
                    "自信に満ちたエネルギーが漂っています。自己PRや面接の準備もスラスラ進み、未来への期待が高まる大吉日！"
                ],
                '50': [
                    "一歩一歩、着実に前へ進んでいる素晴らしい日々です。焦らず自分のペースで企業や働き方をリサーチすると良い発見があります。",
                    "「探している過程」そのものがあなたの経験値になっています。今日学んだことや感じたことをメモしておくと吉。"
                ],
                '10': [
                    "就活はエネルギーを使う大変な大事業です。今日は就活のことは完全に忘れて、好きな映画や本を見て心を解放してください！",
                    "結果や進捗に囚われる必要はありません。今まで踏ん張ってきたあなた自身を全力で肯定し、思いっきりダラダラ過ごしましょう。"
                ]
            }
        };

        // 星座データベース
        const zodiacData = {
            none: "夜空に輝く無数の星々が、今日のあなたの歩む道を優しく照らしています。直感を信じて一歩踏み出してみましょう。",
            aries: "【牡羊座】直感力が高まっています！「楽しそう！」と心が動いた方向へ素直に進むと幸運をつかめます。",
            taurus: "【牡牛座】五感を満たすことで運気がぐんとアップ！美味しい食べ物や良い香りをゆっくり楽しんで。",
            gemini: "【双子座】フットワーク軽く好奇心の赴くままに行動して吉。気軽な雑談や新しい情報にラッキーが隠れています。",
            cancer: "【蟹座】心温まる身近な時間や自分の部屋を心地よく整えることが、明日へのパワーに繋がります。",
            leo: "【獅子座】あなたの自然な笑顔と明るさが周囲を照らします。自分らしさを堂々と表現して楽しもう！",
            virgo: "【乙女座】一歩引いて全体を観察できる落ち着きがあります。自分のペ一スで整理整頓すると気持ちすっきり。",
            libra: "【天秤座】人とのつながりや調和から素敵な刺激をもらえる日。お気に入りの服を着てお出かけもおすすめ。",
            scorpio: "【蠍座】一つのことにじっくり集中できる高い探求心が発揮されます。マイワールドを全力で楽しんで！",
            sagittarius: "【射手座】広い視野と冒険心がワクワクを引き寄せます。普段読まない本や違う道を歩いてみると好展開。",
            capricorn: "【山羊座】積み重ねてきた努力が形になりやすい日。焦らず着実な一歩を進めるあなたに星の祝福があります。",
            aquarius: "【水瓶座】ユニークな発想やアイデアが冴える日。周りと違っても自分ならではの視点を大切にしてOK！",
            pisces: "【魚座】豊かな想像力と優しさが溢れる一日。音楽やアートに触れるとココロが深く癒やされます。"
        };

        const luckyItems = [
            "温かいほうじ茶（またはカフェラテ）",
            "お気に入りの文房具・ペン",
            "フワフワの手触りのタオルやハンカチ",
            "コンビニの新作スイーツ・チョコレート",
            "ミント系のタブレットやリップクリーム",
            "スマホのお気に入りプレイリスト",
            "デスクの隅に置いた小さな観葉植物や雑貨"
        ];

        const healingSpells = {
            '100': "「私の可能性は無限大！今日も最高の一日にしよう」",
            '50': "「できることを、できるペースで。今のままで大丈夫」",
            '10': "「今日も今日とてよく頑張った！偉すぎるぞ、私！」"
        };

        const quests = [
            "自販機やコンビニで「いつもと違う飲み物」を買ってみる",
            "深呼吸をゆっくり3回して、肩の力をふっと抜く",
            "空を見上げて、雲の形を5秒間眺めてみる",
            "今日頑張った自分に向けて、心の中で『おつかれさま』と言う",
            "お気に入りの靴や靴下を履いて出かける",
            "温かいお湯で丁寧に手を洗う"
        ];

        // イベント設定
        document.querySelectorAll('#job-options .option-card').forEach(card => {
            card.addEventListener('click', () => {
                document.querySelectorAll('#job-options .option-card').forEach(c => c.classList.remove('selected'));
                card.classList.add('selected');
                selectedJob = card.dataset.value;
            });
        });

        document.querySelectorAll('#hp-options .option-card').forEach(card => {
            card.addEventListener('click', () => {
                document.querySelectorAll('#hp-options .option-card').forEach(c => c.classList.remove('selected'));
                card.classList.add('selected');
                selectedHp = card.dataset.value;
            });
        });

        const btnFortune = document.getElementById('btn-fortune');
        const resultArea = document.getElementById('result-area');
        const btnReset = document.getElementById('btn-reset');

        btnFortune.addEventListener('click', () => {
            // ランダム選出 & 取得
            const fortunesList = fortuneData[selectedJob][selectedHp];
            const fortuneText = fortunesList[Math.floor(Math.random() * fortunesList.length)];
            
            const selectedZodiac = document.getElementById('zodiac-select').value;
            const zodiacText = zodiacData[selectedZodiac] || zodiacData['none'];

            const itemText = luckyItems[Math.floor(Math.random() * luckyItems.length)];
            const spellText = healingSpells[selectedHp];
            const questText = quests[Math.floor(Math.random() * quests.length)];

            // 結果を画面にセット
            document.getElementById('res-fortune').innerText = fortuneText;
            document.getElementById('res-zodiac').innerText = zodiacText;
            document.getElementById('res-item').innerText = itemText;
            document.getElementById('res-spell').innerText = spellText;
            document.getElementById('res-quest').innerText = questText;

            resultArea.style.display = 'block';
            resultArea.scrollIntoView({ behavior: 'smooth' });
        });

        btnReset.addEventListener('click', () => {
            resultArea.style.display = 'none';
            window.scrollTo({ top: 0, behavior: 'smooth' });
        });
    </script>
</body>
</html>
