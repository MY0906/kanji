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
        background-color: #ffffff !important;
        font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
        overflow-x: hidden;
        max-width: 100% !important;
        box-shadow: none !important;
    }

    /* 一覧全体のレイアウト */
    #list-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        background-color: #ffffff;
    }

    /* 【上の方】普通の白背景の漢字エリア */
    .section-white {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 50px;
        padding: 60px 20px 0px 20px;
        background-color: #ffffff;
    }

    /* 【滑らかな変化を生み出すグラデーションブリッジ】 */
    .gradient-bridge {
        width: 100%;
        padding: 120px 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-sizing: border-box;
        background: linear-gradient(
            to bottom,
            #ffffff 0%,
            #f2f2f2 15%,
            #cdcdcd 35%,
            #777777 50%,
            #333333 65%,
            #111111 85%,
            #000000 100%
        );
        transition: background 0.2s linear;
        position: relative;
    }

    /* 【下の方】黒背景の漢字エリア */
    .section-black {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 50px;
        padding: 0px 20px 300px 20px;
        background-color: #000000;
    }

    /* 漢字カードのデザイン */
    .kanji-card {
        width: 85vw;
        max-width: 450px;
        background-color: transparent !important;
        border: none !important;
        box-shadow: none !important;
        padding: 0 !important;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-sizing: border-box;
        cursor: pointer;
        transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1), filter 0.4s ease;
    }

    /* スクロールで中央に来た時の強調 */
    .kanji-card.active {
        transform: scale(1.04);
    }

    /* 「深」特別な演出用スタイル */
    .kanji-card.special-fuka {
        transition: transform 0.3s ease, filter 0.3s ease;
    }
    .kanji-card.special-fuka.active {
        transform: scale(1.06);
        filter: drop-shadow(0 0 20px rgba(255, 255, 255, 0.4));
    }

    /* 動画・画像表示枠 */
    .media-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        background-color: transparent;
        position: relative;
        pointer-events: none; 
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .kanji-video, .kanji-img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        -webkit-user-select: none;
        user-select: none;
    }

    /* 詳細画面 */
    #video-page {
        position: fixed !important;
        top: 0 !important;
        left: 0 !important;
        width: 100vw !important;
        height: 100vh !important;
        display: none;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        z-index: 999999 !important;
    }

    #video-page.bg-white { background-color: #ffffff !important; }
    #video-page.bg-black { background-color: #000000 !important; }
    
    #video-page.bg-gradient { 
        background: linear-gradient(
            to bottom,
            #111111 0%,
            #333333 40%,
            #111111 80%,
            #000000 100%
        ) !important; 
    }
    
    #video-page.bg-white .description-text { color: #333333; }
    #video-page.bg-black .description-text { color: #ffffff; }
    #video-page.bg-gradient .description-text { color: #ffffff; text-shadow: 0 2px 6px rgba(0,0,0,0.9); }

    .media-container {
        width: 80vw;
        height: 55vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    #main-kanji-video, #main-kanji-img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        pointer-events: none;
        -webkit-user-select: none;
        user-select: none;
    }
    
    .description-text {
        font-size: 1.6rem;
        margin-top: 30px;
        text-align: center;
        max-width: 80%;
        line-height: 1.7;
        font-weight: 500;
    }

    /* 戻るボタン */
    .back-btn {
        position: absolute;
        top: 30px;
        left: 30px;
        font-size: 1.3rem;
        padding: 10px 24px;
        border-radius: 30px;
        cursor: pointer;
        user-select: none;
        z-index: 1000000 !important;
        font-weight: bold;
    }
    #video-page.bg-white .back-btn {
        background-color: #333333;
        color: #ffffff;
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    #video-page.bg-black .back-btn,
    #video-page.bg-gradient .back-btn {
        background-color: #ffffff;
        color: #111111;
        box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    }
</style>

<!-- 一覧画面 -->
<div id="list-page">
    
    <!-- 1. 【上の方】白背景エリア -->
    <div class="section-white">
        
        <div class="kanji-card" onclick="openDetail('雨', '雨.mp4', '空から水滴がぽつぽつと降ってくる様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="雨.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('羽', '羽.mp4', '鳥のふさふさとしたはねが並んでいる様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="羽.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('寒', '寒.mp4', '家の中で人がわらの中にくるまって、凍えている様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="寒.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('叫', '叫.mp4', '口を大きく開けて、大きな声を張り上げてさけぶ様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="叫.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('糸', '糸.mp4', '細い糸を何本かつむいで、束ねた形からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="糸.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('集', '集.mp4', '木の上にたくさんの鳥が集まって止まっている様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="集.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('暑', '暑.mp4', '太陽（日）が照りつけて、お墓の上の人もうだるほどあつい様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="暑.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('木', '木.mp4', '大地にしっかりと根を張り、枝を広げた一本の木の形からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="木.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('目', '目.mp4', '人間の目の形（ひとみとまぶた）を縦にした形からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="目.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('嵐', '嵐.mp4', '山の上を激しい風と雨が吹き荒れる様子からできた漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="嵐.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('林', '林.mp4', '木が２本並んで、木がたくさん生えている場所を表す漢字です。', 'white', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="林.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

    </div>

    <!-- 2. 【深】背景透過PNGを使用した動的グラデーションエリア -->
    <div class="gradient-bridge" id="bridge-zone">
        <div class="kanji-card special-fuka" id="fuka-card" onclick="openDetail('深', '深.png', '川の水が底深く流れていて、中に探り入れる様子からできた漢字です。', 'gradient', 'image')">
            <div class="media-wrapper">
                <img class="kanji-img" src="深.png" alt="深">
            </div>
        </div>
    </div>

    <!-- 3. 【下の方】黒背景エリア -->
    <div class="section-black">
        
        <div class="kanji-card" onclick="openDetail('明', '明.mp4', '太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="明.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('眩', '眩.mp4', '目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="眩.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('影', '影2.mp4', '光が当たって物に遮られ、うしろに黒く浮かび上がる様子からできた漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="影2.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('幻', '幻.mp4', '糸が絡み合って形がころころと変わり、姿をくらます様子からできた漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="幻.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('光', '光.mp4', '人が頭の上に松明（たいまつ）を載せて、周りをピカッと照らしている様子からできた漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="光.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

        <div class="kanji-card" onclick="openDetail('星', '星.mp4', '太陽（日）のもとで、芽（生）がすくすくと育つように夜空にきらきら光る星を表す漢字です。', 'black', 'video')">
            <div class="media-wrapper">
                <video class="kanji-video" src="星.mp4" playsinline muted loop preload="metadata"></video>
            </div>
        </div>

    </div>

</div>

<!-- 詳細画面 -->
<div id="video-page">
    <div class="back-btn" onclick="closeDetail()">← もどる</div>
    <div class="media-container" id="detail-media-container">
        <video id="main-kanji-video" src="" playsinline loop style="display: none;"></video>
        <img id="main-kanji-img" src="" alt="" style="display: none;">
    </div>
    <div class="description-text" id="kanji-desc"></div>
</div>

<script>
    const listPage = document.getElementById('list-page');
    const videoPage = document.getElementById('video-page');
    const mainKanjiVideo = document.getElementById('main-kanji-video');
    const mainKanjiImg = document.getElementById('main-kanji-img');
    const kanjiDesc = document.getElementById('kanji-desc');
    const bridgeZone = document.getElementById('bridge-zone');
    const fukaCard = document.getElementById('fuka-card');

    let savedScrollPosition = 0;

    // スクロールに応じた「深」エリアの動的グラデーション計算
    window.addEventListener('scroll', () => {
        if (!bridgeZone || !fukaCard) return;

        const rect = bridgeZone.getBoundingClientRect();
        const windowHeight = window.innerHeight;

        let progress = (windowHeight - rect.top) / (windowHeight + rect.height);
        progress = Math.max(0, Math.min(1, progress));

        const midPoint = Math.round(progress * 100);
        const startPoint = Math.max(0, midPoint - 30);
        const endPoint = Math.min(100, midPoint + 30);

        bridgeZone.style.background = `linear-gradient(
            to bottom,
            #ffffff 0%,
            #cccccc ${startPoint}%,
            #555555 ${midPoint}%,
            #000000 ${endPoint}%
        )`;
    });

    // 詳細ページを開く（動画と画像の両方に対応）
    function openDetail(kanjiName, mediaFile, description, bgType, mediaType = 'video') {
        savedScrollPosition = window.scrollY || document.documentElement.scrollTop;

        listPage.style.display = 'none';
        videoPage.style.display = 'flex';
        
        videoPage.className = '';
        if (bgType === 'white') {
            videoPage.classList.add('bg-white');
        } else if (bgType === 'gradient') {
            videoPage.classList.add('bg-gradient');
        } else {
            videoPage.classList.add('bg-black');
        }
        
        if (mediaType === 'image') {
            mainKanjiVideo.style.display = 'none';
            mainKanjiVideo.pause();
            mainKanjiImg.src = mediaFile;
            mainKanjiImg.style.display = 'block';
        } else {
            mainKanjiImg.style.display = 'none';
            mainKanjiVideo.src = mediaFile;
            mainKanjiVideo.style.display = 'block';
            mainKanjiVideo.currentTime = 0;
            mainKanjiVideo.play().catch(e => console.log("Play blocked: ", e));
        }

        kanjiDesc.innerHTML = `<span style="font-size: 2.2rem; font-weight: bold;">${kanjiName}</span><br><br>${description}`;
    }

    // 元の一覧ページに戻る
    function closeDetail() {
        mainKanjiVideo.pause();
        listPage.style.display = 'flex';
        videoPage.style.display = 'none';

        window.scrollTo(0, savedScrollPosition);
    }

    // スクロール時の制御
    const options = {
        root: null,
        rootMargin: "-30% 0px -30% 0px",
        threshold: 0.3
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            const card = entry.target;
            const video = card.querySelector('.kanji-video');

            if (entry.isIntersecting) {
                card.classList.add('active');
                if (video) video.play().catch(e => console.log("Preview play blocked: ", e));
            } else {
                card.classList.remove('active');
                if (video) {
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
