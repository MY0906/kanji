<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>漢字の学習ツール</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #f7f9fa;
            font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
            overflow-x: hidden;
        }
        #list-page {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 30px;
            padding: 40px;
            justify-items: center;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }
        .kanji-btn {
            font-size: 6rem;
            color: #333333;
            cursor: pointer;
            transition: transform 0.2s;
            user-select: none;
            text-align: center;
        }
        .kanji-btn:active {
            transform: scale(0.9);
        }
        #video-page {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: #ffffff;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .video-container {
            width: 80vw;
            height: 60vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        video {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        .description-text {
            font-size: 1.8rem;
            color: #444444;
            margin-top: 20px;
            text-align: center;
            max-width: 70%;
            line-height: 1.6;
        }
        .back-btn {
            position: absolute;
            top: 30px;
            left: 30px;
            font-size: 1.5rem;
            padding: 10px 25px;
            background-color: #333333;
            color: white;
            border-radius: 30px;
            cursor: pointer;
            user-select: none;
        }
    </style>
</head>
<body>

    <!-- 一覧画面 -->
    <div id="list-page">
        <div class="kanji-btn" onclick="playVideo('雨', '空から水滴がぽつぽつと降ってくる様子からできた漢字です。')">雨</div>
        <div class="kanji-btn" onclick="playVideo('羽', '鳥のふさふさとしたはねが並んでいる様子からできた漢字です。')">羽</div>
        <div class="kanji-btn" onclick="playVideo('寒', '家の中で人がわらの中にくるまって、凍えている様子からできた漢字です。')">寒</div>
        <div class="kanji-btn" onclick="playVideo('叫', '口を大きく開けて、大きな声を張り上げてさけぶ様子からできた漢字です。')">叫</div>
        <div class="kanji-btn" onclick="playVideo('月', '夜空に浮かぶ美しい三日月の形からできた漢字です。')">月</div>
        <div class="kanji-btn" onclick="playVideo('糸', '細い糸を何本かつむいで、束ねた形からできた漢字です。')">糸</div>
        <div class="kanji-btn" onclick="playVideo('集', '木の上にたくさんの鳥が集まって止まっている様子からできた漢字です。')">集</div>
        <div class="kanji-btn" onclick="playVideo('暑', '太陽（日）が照りつけて、お墓の上の人もうだるほどあつい様子からできた漢字です。')">暑</div>
        <div class="kanji-btn" onclick="playVideo('明', '太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。')">明</div>
        <div class="kanji-btn" onclick="playVideo('木', '大地にしっかりと根を張り、枝を広げた一本の木の形からできた漢字です。')">木</div>
        <div class="kanji-btn" onclick="playVideo('目', '人間の目の形（ひとみとまぶた）を縦にした形からできた漢字です。')">目</div>
        <div class="kanji-btn" onclick="playVideo('嵐', '山の上を激しい風と雨が吹き荒れる様子からできた漢字です。')">嵐</div>
        <div class="kanji-btn" onclick="playVideo('林', '木が２本並んで、木がたくさん生えている場所を表す漢字です。')">林</div>
        <div class="kanji-btn" onclick="playVideo('眩', '目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。')">眩</div>
    </div>

    <!-- 詳細画面 -->
    <div id="video-page">
        <div class="back-btn" onclick="backToList()">← もどる</div>
        <div class="video-container">
            <video id="kanji-video" src="" playsinline></video>
        </div>
        <div class="description-text" id="kanji-desc"></div>
    </div>

    <script>
        const listPage = document.getElementById('list-page');
        const videoPage = document.getElementById('video-page');
        const kanjiVideo = document.getElementById('kanji-video');
        const kanjiDesc = document.getElementById('kanji-desc');

        function playVideo(kanjiName, description) {
            listPage.style.display = 'none';
            videoPage.style.display = 'flex';
            
            kanjiVideo.src = kanjiName + ".mp4";
            kanjiDesc.innerHTML = `<strong>${kanjiName}</strong><br>${description}`;
            
            kanjiVideo.currentTime = 0;
            kanjiVideo.play();
        }

        function backToList() {
            kanjiVideo.pause();
            // 【修正ポイント】戻るときに「flex」ではなく「grid」を指定して、最初の配置をキープさせます
            listPage.style.display = 'grid';
            videoPage.style.display = 'none';
        }
    </script>
</body>
</html>
