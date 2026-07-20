<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <style>
        header,
        .markdown-body header,
        body > h1:first-of-type,
        body > p:first-of-type,
        .markdown-body > h1:first-child,
        #header-container,
        .content-header,
        .gh-header {
            display: none !important;
            height: 0 !important;
            padding: 0 !important;
            margin: 0 !important;
            opacity: 0 !important;
            visibility: hidden !important;
        }

        html, body, .markdown-body {
            margin: 0 !important;
            padding: 0 !important;
            background-color: #f7f9fa !important;
            font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
            overflow-x: hidden;
            max-width: 100% !important;
            box-shadow: none !important;
        }

        #list-page {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 30px;
            padding: 40px;
            justify-items: center;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            background-color: #f7f9fa;
        }

        .kanji-thumb-container {
            width: 160px;
            height: 160px;
            cursor: pointer;
            position: relative;
            border-radius: 12px;
            overflow: hidden;
            background-color: #fff;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }
        .kanji-thumb-container:hover {
            transform: scale(1.05);
        }

        .kanji-video-thumb {
            width: 100%;
            height: 100%;
            object-fit: contain;
            user-select: none;
            pointer-events: none;
        }

        #video-page {
            position: fixed !important;
            top: 0 !important;
            left: 0 !important;
            width: 100vw !important;
            height: 100vh !important;
            background-color: #ffffff !important;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 999999 !important;
        }
        .video-container {
            width: 80vw;
            height: 60vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        video#main-kanji-video {
            width: 100%;
            height: 100%;
            object-fit: contain;
            pointer-events: none;
            -webkit-user-select: none;
            user-select: none;
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
            z-index: 1000000 !important;
        }
    </style>
</head>
<body>

    <div id="list-page">
        <div class="kanji-thumb-container" onclick="openDetail('雨', '空から水滴がぽつぽつと降ってくる様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="雨.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('羽', '鳥のふさふさとしたはねが並んでいる様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="羽.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('寒', '家の中で人がわらの中にくるまって、凍えている様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="寒.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('叫', '口を大きく開けて、大きな声を張り上げてさけぶ様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="叫.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('月', '夜空に浮かぶ美しい三日月の形からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="月.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('糸', '細い糸を何本かつむいで、束ねた形からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="糸.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('集', '木の上にたくさんの鳥が集まって止まっている様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="集.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('暑', '太陽（日）が照りつけて、お墓の上の人もうだるほどあつい様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="暑.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('明', '太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="明.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('木', '大地にしっかりと根を張り、枝を広げた一本の木の形からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="木.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('目', '人間の目の形（ひとみとまぶた）を縦にした形からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="目.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('嵐', '山の上を激しい風と雨が吹き荒れる様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="嵐.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('林', '木が２本並んで、木がたくさん生えている場所を表す漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="林.mp4" playsinline muted preload="metadata"></video>
        </div>
        <div class="kanji-thumb-container" onclick="openDetail('眩', '目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。')" onmouseover="startPreview(this)" onmouseout="stopPreview(this)">
            <video class="kanji-video-thumb" src="眩.mp4" playsinline muted preload="metadata"></video>
        </div>
    </div>

    <div id="video-page">
        <div class="back-btn" onclick="closeDetail()">← もどる</div>
        <div class="video-container">
            <video id="main-kanji-video" src="" playsinline loop></video>
        </div>
        <div class="description-text" id="kanji-desc"></div>
    </div>

    <script>
        const listPage = document.getElementById('list-page');
        const videoPage = document.getElementById('video-page');
        const mainKanjiVideo = document.getElementById('main-kanji-video');
        const kanjiDesc = document.getElementById('kanji-desc');

        function startPreview(container) {
            const videoThumb = container.querySelector('.kanji-video-thumb');
            videoThumb.currentTime = 0;
            videoThumb.play().catch(e => console.log("Preview play blocked: ", e));
        }

        function stopPreview(container) {
            const videoThumb = container.querySelector('.kanji-video-thumb');
            videoThumb.pause();
            videoThumb.currentTime = 0;
        }

        function openDetail(kanjiName, description) {
            listPage.style.display = 'none';
            videoPage.style.display = 'flex';
            
            mainKanjiVideo.src = kanjiName + ".mp4";
            kanjiDesc.innerHTML = `<strong>${kanjiName}</strong><br>${description}`;
            
            mainKanjiVideo.currentTime = 0;
            mainKanjiVideo.play().catch(e => console.log("Play blocked: ", e));
        }

        function closeDetail() {
            mainKanjiVideo.pause();
            listPage.style.display = 'grid';
            videoPage.style.display = 'none';
        }
    </script>
</body>
</html>
