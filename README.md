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
        background-color: #f7f9fa !important;
        font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
        overflow-x: hidden;
        max-width: 100% !important;
        box-shadow: none !important;
    }

    /* 【一覧画面】iPad用の縦一列並びレイアウト */
    #list-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 50px;
        padding: 40px 20px 200px 20px;
        max-width: 800px;
        margin: 0 auto;
        background-color: #f7f9fa;
    }

    /* 漢字カード本体（タップで詳細へ飛ぶ） */
    .kanji-card {
        width: 90vw;
        max-width: 500px;
        background-color: #ffffff;
        border-radius: 24px;
        box-shadow: 0 8px 24px rgba(0,0,0,0.06);
        padding: 30px;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-sizing: border-box;
        transition: transform 0.3s, box-shadow 0.3s;
        cursor: pointer;
    }

    .kanji-card.active {
        transform: scale(1.02);
        box-shadow: 0 12px 32px rgba(0,0,0,0.1);
    }

    /* 動画を表示するエリア（タップを貫通させてカード全体のクリックにする） */
    .video-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        border-radius: 16px;
        overflow: hidden;
        background-color: #ffffff;
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
        background-color: #ffffff !important;
        display: none; /* 最初は隠しておく */
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
    
    /* 詳細画面の動画も誤作動（干渉）を完全に防ぐ */
    video#main-kanji-video {
        width: 100%;
        height: 100%;
        object-fit: contain;
        pointer-events: none;
        -webkit-user-select: none;
        user-select: none;
    }
    
    /* 詳細画面に表示される説明文 */
    .description-text {
        font-size: 1.8rem;
        color: #444444;
        margin-top: 20px;
        text-align: center;
        max-width: 70%;
        line-height: 1.6;
    }

    /* 左上の「もどる」ボタン */
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

<!-- 一覧画面（1字ずつ縦に並び、タップで詳細ページへ移動する） -->
<div id="list-page">
    
    <div class="kanji-card" onclick="openDetail('雨', '空から水滴がぽつぽつと降ってくる様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="雨.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('羽', '鳥のふさふさとしたはねが並んでいる様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="羽.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('寒', '家の中で人がわらの中にくるまって、凍えている様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="寒.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('叫', '口を大きく開けて、大きな声を張り上げてさけぶ様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="叫.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('月', '夜空に浮かぶ美しい三日月の形からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="月.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('糸', '細い糸を何本かつむいで、束ねた形からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="糸.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('集', '木の上にたくさんの鳥が集まって止まっている様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="集.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('暑', '太陽（日）が照りつけて、お墓の上の人もうだるほどあつい様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="暑.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('明', '太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="明.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('木', '大地にしっかりと根を張り、枝を広げた一本の木の形からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="木.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('目', '人間の目の形（ひとみとまぶた）を縦にした形からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="目.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('嵐', '山の上を激しい風と雨が吹き荒れる様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="嵐.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('林', '木が２本並んで、木がたくさん生えている場所を表す漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="林.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

    <div class="kanji-card" onclick="openDetail('眩', '目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。')">
        <div class="video-wrapper">
            <video class="kanji-video" src="眩.mp4" playsinline muted loop preload="metadata"></video>
        </div>
    </div>

</div>

<!-- 詳細画面（隠しページ：タップされたらここが大画面で開きます） -->
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
        listPage.style.display = 'none'; // 一覧を隠す
        videoPage.style.display = 'flex'; // 詳細ページを表示
        
        mainKanjiVideo.src = kanjiName + ".mp4"; // 動画をセット
        kanjiDesc.innerHTML = `<strong>${kanjiName}</strong><br>${description}`; // 説明文をセット
        
        mainKanjiVideo.currentTime = 0;
        mainKanjiVideo.play().catch(e => console.log("Play blocked: ", e));
    }

    // 元の一覧ページにもどる関数
    function closeDetail() {
        mainKanjiVideo.pause();
        listPage.style.display = 'flex'; // 一覧を再表示
        videoPage.style.display = 'none'; // 詳細ページを隠す
    }

    // iPadのスクロールに合わせて一覧画面の動画を自動再生・停止する設定
    const options = {
        root: null,
        rootMargin: "-30% 0px -30% 0px",
        threshold: 0.5
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
