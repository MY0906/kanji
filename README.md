<style>
    /* GitHubが自動生成する余計な文字やヘッダーを完全に隠す */
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
        background-color: #111111 !important; /* 全体を真っ黒なスクリーンに */
        font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
        overflow-x: hidden;
        max-width: 100% !important;
        box-shadow: none !important;
    }

    /* 【一覧画面】黒背景の全体レイアウト */
    #list-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 60px;
        padding: 80px 20px 200px 20px;
        max-width: 800px;
        margin: 0 auto;
        background-color: #111111;
    }

    /* 漢字カード（枠や影を完全に無くし、動画そのものが浮いているように変更） */
    .kanji-card {
        width: 85vw;
        max-width: 450px;
        background-color: transparent !important; /* 背景枠を完全に透明に */
        border: none !important;
        box-shadow: none !important;
        padding: 0 !important;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-sizing: border-box;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    /* スクロール中央に来た時にほんの少しだけ大きくして見やすく */
    .kanji-card.active {
        transform: scale(1.03);
    }

    /* 動画を表示するエリア */
    .video-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        background-color: transparent;
        position: relative;
        pointer-events: none; 
    }

    .kanji-video {
        width: 100%;
        height: 100%;
        object-fit: contain;
        -webkit-user-select: none;
        user-select: none;
    }

    /* 【詳細画面】タップした後に大きく表示されるページ */
    #video-page {
        position: fixed !important;
        top: 0 !important;
        left: 0 !important;
        width: 100vw !important;
        height: 100vh !important;
        background-color: #111111 !important; /* 詳細画面も黒背景に統一 */
        display: none;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        z-index: 999999 !important;
    }

    .video-container {
        width: 80vw;
        height: 55vh;
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
    
    /* 詳細画面の説明文（黒背景で見えやすいよう文字は白に） */
    .description-text {
        font-size: 1.6rem;
        color: #ffffff;
        margin-top: 30px;
        text-align: center;
        max-width: 80%;
        line-height: 1.7;
        font-weight: 500;
    }

    /* 左上の「もどる」ボタン（黒背景で見えやすいよう白ボタンに） */
    .back-btn {
        position: absolute;
        top: 30px;
        left: 30px;
        font-size: 1.3rem;
        padding: 10px 24px;
        background-color: #ffffff;
        color: #111111;
        border-radius: 30px;
        cursor: pointer;
        user-select: none;
        z-index: 1000000 !important;
        box-shadow: 0 4px 12px rgba(0,0,0,0.3);
        font-weight: bold;
    }
</style>

<!-- 一覧画面（「明」と「眩」の2つだけにまとめて黒背景に配置） -->
<div id="list-page">
    
    <!-- 1つ目：明 -->
    <div class="kanji-card" onclick="openDetail('明', '太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="明.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <!-- 2つ目：眩 -->
    <div class="kanji-card" onclick="openDetail('眩', '目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="眩.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

</div>

<!-- 詳細画面（タップすると開く黒背景のページ） -->
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

    // 詳細ページを開く関数
    function openDetail(kanjiName, description) {
        listPage.style.display = 'none';
        videoPage.style.display = 'flex';
        
        mainKanjiVideo.src = kanjiName + ".mp4";
        kanjiDesc.innerHTML = `<span style="font-size: 2.2rem; font-weight: bold;">${kanjiName}</span><br><br>${description}`;
        
        mainKanjiVideo.currentTime = 0;
        mainKanjiVideo.play().catch(e => console.log("Play blocked: ", e));
    }

    // 元の一覧ページにもどる関数
    function closeDetail() {
        mainKanjiVideo.pause();
        listPage.style.display = 'flex';
        videoPage.style.display = 'none';
    }

    // iPadのスクロール自動再生の設定
    const options = {
        root: null,
        rootMargin: "-35% 0px -35% 0px",
        threshold: 0.4
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            const card = entry.target;
            const video = card.querySelector('.kanji-video');

            if (video) {
                if (entry.isIntersecting) {
                    card.classList.add('active');
                    video.play().catch(e => console.log("Preview play blocked: ", e));
                } else {
                    card.classList.remove('active');
                    video.pause();
                    video.currentTime = 0;
                }
            }
        });
    }, options);

    document.querySelectorAll('.kanji-card').forEach(card => {
        observer.observe(card);
    });
</script>
