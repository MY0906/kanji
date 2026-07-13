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
            overflow: hidden;
        }
        #list-page {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            gap: 40px;
        }
        .kanji-btn {
            font-size: 8rem;
            color: #333333;
            cursor: pointer;
            transition: transform 0.2s;
            user-select: none;
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

    <div id="list-page">
        <div class="kanji-btn" onclick="playVideo()">雨</div>
    </div>

    <div id="video-page">
        <div class="back-btn" onclick="backToList()">← もどる</div>
        <div class="video-container">
            <video id="ame-video" src="雨.mp4" playsinline></video>
        </div>
        <div class="description-text">
            <strong>雨（あめ）</strong><br>
            空から水滴がぽつぽつと降ってくる様子からできた漢字です。
        </div>
    </div>

    <script>
        const listPage = document.getElementById('list-page');
        const videoPage = document.getElementById('video-page');
        const ameVideo = document.getElementById('ame-video');

        function playVideo() {
            listPage.style.display = 'none';
            videoPage.style.display = 'flex';
            ameVideo.currentTime = 0;
            ameVideo.play();
        }

        function backToList() {
            ameVideo.pause();
            listPage.style.display = 'flex';
            videoPage.style.display = 'none';
        }
    </script>
</body>
</html>
