<style>
    /* GitHubヘッダー隠し */
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

    #list-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        background-color: #ffffff;
    }

    /* 白背景エリア */
    .section-white {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 50px;
        padding: 60px 20px 0px 20px;
        background-color: #ffffff;
    }

    /* 広域で超滑らかなグラデーションブリッジエリア */
    .gradient-bridge {
        width: 100%;
        padding: 250px 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        box-sizing: border-box;
        background: linear-gradient(
            to bottom,
            #ffffff 0%,
            #f7f7f7 10%,
            #e3e3e3 22%,
            #c4c4c4 35%,
            #999999 48%,
            #666666 62%,
            #383838 75%,
            #181818 88%,
            #000000 100%
        );
        will-change: background;
        position: relative;
    }

    /* 黒背景エリア */
    .section-black {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 50px;
        padding: 0px 20px 300px 20px;
        background-color: #000000;
    }

    /* 漢字カード基本構造 */
    .kanji-card {
        width: 85vw;
        max-width: 450px;
        background: transparent !important;
        background-color: transparent !important;
        border: none !important;
        outline: none !important;
        box-shadow: none !important;
        padding: 0 !important;
        display: flex;
        flex-direction: column;
        align-items: center;
        box-sizing: border-box;
        cursor: pointer;
        transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1), filter 0.4s ease;
    }

    .kanji-card.active {
        transform: scale(1.04);
    }

    /* 「深」カード専用のコンパクトな泡エリア */
    .bubble-stage-compact {
        width: 85vw;
        max-width: 450px;
        aspect-ratio: 1 / 1;
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
        box-sizing: border-box;
    }

    /* シンプル＆フラットな泡のスタイル */
    .sea-bubble {
        position: absolute;
        bottom: -20px;
        background: rgba(255, 255, 255, 0.15);
        border: 1.5px solid rgba(255, 255, 255, 0.6);
        border-radius: 50%;
        pointer-events: none;
        animation: floatUp 6s infinite ease-in-out;
        will-change: transform, opacity;
    }

    /* 泡の上昇アニメーション（一覧用） */
    @keyframes floatUp {
        0% {
            transform: translateY(0) translateX(0);
            opacity: 0;
        }
        20% {
            opacity: 0.8;
        }
        80% {
            opacity: 0.6;
        }
        100% {
            transform: translateY(-460px) translateX(15px);
            opacity: 0;
        }
    }

    /* 詳細画面用の泡アニメーション */
    @keyframes floatUpDetail {
        0% {
            transform: translateY(0) translateX(0);
            opacity: 0;
        }
        20% {
            opacity: 0.8;
        }
        80% {
            opacity: 0.6;
        }
        100% {
            transform: translateY(-55vh) translateX(20px);
            opacity: 0;
        }
    }

    .sea-bubble-detail {
        position: absolute;
        bottom: -20px;
        background: rgba(255, 255, 255, 0.2);
        border: 1.5px solid rgba(255, 255, 255, 0.7);
        border-radius: 50%;
        pointer-events: none;
        animation: floatUpDetail 6s infinite ease-in-out;
        will-change: transform, opacity;
        z-index: 1;
    }

    /* 「深」カードのインタラクティブ演出 */
    .kanji-card.special-fuka {
        width: 100%;
        height: 100%;
        z-index: 10;
        transition: transform 0.2s cubic-bezier(0.1, 0.8, 0.3, 1), filter 0.2s cubic-bezier(0.1, 0.8, 0.3, 1);
        will-change: transform, filter;
    }

    .media-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        background: transparent !important;
        background-color: transparent !important;
        position: relative;
        pointer-events: none; 
        display: flex;
        justify-content: center;
        align-items: center;
        border: none !important;
        box-shadow: none !important;
    }

    .kanji-video {
        width: 100%;
        height: 100%;
        object-fit: contain;
        background: transparent !important;
        -webkit-user-select: none;
        user-select: none;
    }

    .kanji-img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        background: transparent !important;
        background-color: transparent !important;
        border: none !important;
        outline: none !important;
        box-shadow: none !important;
        -webkit-user-select: none;
        user-select: none;
        mix-blend-mode: normal !important;
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
        padding: 40px 20px 20px 20px;
        box-sizing: border-box;
        z-index: 999999 !important;
    }

    #video-page.bg-white { background-color: #ffffff !important; }
    #video-page.bg-black { background-color: #000000 !important; }
    
    #video-page.bg-gradient { 
        background: linear-gradient(
            to bottom,
            #ffffff 0%,
            #e3e3e3 25%,
            #777777 50%,
            #222222 75%,
            #000000 100%
        ) !important; 
    }
    
    #video-page.bg-white .description-text { color: #333333; }
    #video-page.bg-black .description-text { color: #ffffff; }
    #video-page.bg-gradient .description-text { color: #ffffff; text-shadow: 0 2px 8px rgba(0,0,0,0.9); }

    .media-container {
        width: 80vw;
        height: 35vh;
        max-height: 280px;
        display: flex;
        justify-content: center;
        align-items: center;
        background: transparent !important;
        position: relative;
        overflow: hidden;
        flex-shrink: 0;
    }
    
    #main-kanji-video {
        width: 100%;
        height: 100%;
        object-fit: contain;
        pointer-events: none;
        background: transparent !important;
        -webkit-user-select: none;
        user-select: none;
        z-index: 2;
    }

    #main-kanji-img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        pointer-events: none;
        background: transparent !important;
        background-color: transparent !important;
        border: none !important;
        box-shadow: none !important;
        -webkit-user-select: none;
        user-select: none;
        z-index: 2;
    }
    
    .description-text {
        font-size: clamp(0.9rem, 1.8vw, 1.15rem);
        margin-top: 10px;
        text-align: left;
        max-width: 85vw;
        line-height: 1.45;
        font-weight: 500;
        z-index: 2;
        overflow: visible;
    }

    .back-btn {
        position: absolute;
        top: 25px;
        left: 25px;
        font-size: 1.2rem;
        padding: 8px 20px;
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
    
    <div class="section-white">
        <div class="kanji-card" onclick="openDetail('雨', '雨.mp4', 'あめ。あめふり。また、あめのように降り注ぐもの。', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="雨.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('羽', '羽.mp4', '①はね。つばさ。「羽毛」「羽化」「翼羽」<br>②鳥などを数える語。<br>③「出羽(でわ)の国」の略。「羽州」「羽前」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="羽.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('寒', '寒.mp4', '①さむい。つめたい。ぞっとする。「寒色」「寒心」「寒冷」<br>②さびしい。まずしい。いやしい。「寒煙」「寒酸」「寒村」<br>③かん。二十四節気の一つ。立春前のほぼ三〇日間。「寒中」「寒梅」「大寒」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="寒.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('叫', '叫.mp4', 'さけぶ。大声をあげる。「叫喚」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="叫.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('糸', '糸.mp4', '①いと。いとのように細いもの。「金糸」「菌糸」<br>②糸を張った楽器。弦楽器。「糸竹」「糸管」<br>③数量の単位。一の一万分の一。<br>④ごくわずか。「糸毫(シゴウ)」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="糸.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('集', '集.mp4', '①あつまる。あつめる。つどう。よせあつめる。「集散」「集計」「召集」<br>②あつまり。つどい。「集会」「集落」<br>③作品をあつめたもの。「画集」「詩集」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="集.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('暑', '暑.mp4', '①あつい。気温が高い。「暑気」「炎暑」「酷暑」<br>②あつい季節。特に、夏の土用一八日間。「暑中」「大暑」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="暑.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('木', '木.mp4', '①き。たちき。「木石」「樹木」<br>②建築や器具の用材。「木刀」「材木」<br>③五行の一つ。<br>④七曜の一つ。木曜。<br>⑤かざりけがない。「木訥(ボクトツ)」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="木.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('目', '目.mp4', '①め。まなこ。「目前」「耳目」<br>②見る。見つめる。「目撃」「注目」<br>③かなめ。要点。「眼目」「要目」<br>④かしら。主だった人。「頭目」<br>⑤見出し。な。なまえ。「目次」「品目」<br>⑥小分けしたもの。「科目」「項目」<br>⑦生物分類上の一段階。「霊長目」<br>⑧かお。名誉。「面目」<br>⑨いま。ただいま。「目下」<br>⑩きざみ。さかい。すじ。「木目」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="目.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('嵐', '嵐.mp4', '①あらし。激しく吹く風。「山嵐」「春嵐」<br>②山にたちこめる気。もや。「嵐気」「青嵐」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="嵐.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('林', '林.mp4', '①はやし。木やタケが群がり生えている所。「林間」「森林」<br>②物事が多く集まっていること。「林立」「書林」', 'white', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="林.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
    </div>

    <!-- 【深】広域滑らかグラデーション ＆ 泡エリア -->
    <div class="gradient-bridge" id="bridge-zone">
        <div class="bubble-stage-compact" id="bubble-stage">
            <div class="kanji-card special-fuka" id="fuka-card" onclick="openDetail('深', 'hukai_transparent.png', '①底がふかい。「深海」「水深」<br>②おくぶかい。「深遠」「深長」<br>③はなはだしい。「深刻」<br>④ねんごろ。こまやかな。「深交」「深情」<br>⑤色がこい。「深紅」<br>⑥夜がふける。「深更」', 'gradient', 'image')">
                <div class="media-wrapper">
                    <img class="kanji-img" src="hukai_transparent.png" alt="深">
                </div>
            </div>
        </div>
    </div>

    <div class="section-black">
        <div class="kanji-card" onclick="openDetail('明', '明.mp4', '①あかるい。「明星」「清明」<br>②あかり。あかりがつく。「明滅」「灯明」<br>③あきらか。あきらかにする。「明確」「証明」<br>④さとい。かしこい。「明君」「賢明」<br>⑤あける。夜があける。また、つぎの。あす。「明晩」「未明」<br>⑥神。また、神聖なもの。「神明」<br>⑦みん。中国の王朝名。', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="明.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('眩', '眩.mp4', '①くらむ。目が回る。めまい。「眩暈(ゲンウン)」<br>②くらます。まどわす。「眩惑」<br>③まぶしい。まばゆい。<br>④まう。まどう。判断がみだれる。', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="眩.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('影', '影2.mp4', '①かげ。光がさえぎられてできる黒いかげ。「影響」「陰影」<br>②ひかり。日月などのひかり。「月影」「光影」<br>③光に映し出されたすがた。かたち。「影像」「印影」「撮影」<br>④まぼろし。', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="影2.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('幻', '幻.mp4', '①まぼろし。実在しないのに、あるように見えるもの。「幻影」「夢幻」<br>②まどわす。たぶらかす。「幻術」「幻惑」', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="幻.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('光', '光.mp4', '①ひかる。てらす。ひかり。あかり。かがやき。「光線」「光明」「月光」<br>②かがやかしいこと。ほまれ。名声。「光臨」「栄光」<br>③時間。とき。「光陰」「消光」<br>④ありさま。けしき。「光景」「風光」', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="光.mp4" playsinline muted loop preload="metadata"></video></div>
        </div>
        <div class="kanji-card" onclick="openDetail('星', '星.mp4', '①ほし。天体。「星座」「恒星」<br>②とし。年月。「星霜」<br>③重要な人物。「巨星」「将星」<br>④めあて。小さな点。「図星」', 'black', 'video')">
            <div class="media-wrapper"><video class="kanji-video" src="星.mp4" playsinline muted loop preload="metadata"></video></div>
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
    const bubbleStage = document.getElementById('bubble-stage');
    const detailMediaContainer = document.getElementById('detail-media-container');

    let savedScrollPosition = 0;

    /* 一覧用：泡生成 */
    function createBubbles() {
        if (!bubbleStage) return;
        const bubbleCount = 10;
        
        for (let i = 0; i < bubbleCount; i++) {
            const bubble = document.createElement('div');
            bubble.classList.add('sea-bubble');
            
            const size = Math.random() * 12 + 6;
            bubble.style.width = `${size}px`;
            bubble.style.height = `${size}px`;
            
            bubble.style.left = `${Math.random() * 90}%`;
            
            const duration = Math.random() * 3 + 4;
            const delay = Math.random() * 5;
            bubble.style.animationDuration = `${duration}s`;
            bubble.style.animationDelay = `${delay}s`;
            
            bubbleStage.appendChild(bubble);
        }
    }
    createBubbles();

    /* 詳細画面用：泡生成とクリア */
    function createDetailBubbles() {
        clearDetailBubbles();
        if (!detailMediaContainer) return;

        const bubbleCount = 12;
        for (let i = 0; i < bubbleCount; i++) {
            const bubble = document.createElement('div');
            bubble.classList.add('sea-bubble-detail');
            
            const size = Math.random() * 14 + 8;
            bubble.style.width = `${size}px`;
            bubble.style.height = `${size}px`;
            
            bubble.style.left = `${Math.random() * 90}%`;
            
            const duration = Math.random() * 3 + 4;
            const delay = Math.random() * 4;
            bubble.style.animationDuration = `${duration}s`;
            bubble.style.animationDelay = `${delay}s`;
            
            detailMediaContainer.appendChild(bubble);
        }
    }

    function clearDetailBubbles() {
        if (!detailMediaContainer) return;
        const oldBubbles = detailMediaContainer.querySelectorAll('.sea-bubble-detail');
        oldBubbles.forEach(b => b.remove());
    }

    /* 背景パララックス＆「深」演出 */
    window.addEventListener('scroll', () => {
        if (!bridgeZone || !fukaCard) return;

        const bridgeRect = bridgeZone.getBoundingClientRect();
        const cardRect = fukaCard.getBoundingClientRect();
        const windowHeight = window.innerHeight;

        let progress = (windowHeight - bridgeRect.top) / (windowHeight + bridgeRect.height);
        progress = Math.max(0, Math.min(1, progress));

        const easedProgress = Math.pow(progress, 1.1);

        const stop1 = Math.round(easedProgress * 18);
        const stop2 = Math.round(easedProgress * 42);
        const stop3 = Math.round(easedProgress * 68);
        const stop4 = Math.round(easedProgress * 90);

        bridgeZone.style.background = `linear-gradient(
            to bottom,
            #ffffff 0%,
            #f5f5f5 ${stop1}%,
            #d5d5d5 ${stop2}%,
            #707070 ${stop3}%,
            #202020 ${stop4}%,
            #000000 100%
        )`;

        const cardCenter = cardRect.top + cardRect.height / 2;
        const windowCenter = windowHeight / 2;
        
        const distanceFromCenter = Math.abs(windowCenter - cardCenter) / (windowHeight / 2);
        const closeness = Math.max(0, 1 - distanceFromCenter);

        const scale = 1.0 + (closeness * 0.06);
        const shadowBlur = closeness * 30;
        const shadowAlpha = closeness * 0.6;

        fukaCard.style.transform = `scale(${scale})`;
        fukaCard.style.filter = `drop-shadow(0 0 ${shadowBlur}px rgba(255, 255, 255, ${shadowAlpha}))`;
    });

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

        if (kanjiName === '深') {
            createDetailBubbles();
        } else {
            clearDetailBubbles();
        }

        kanjiDesc.innerHTML = `<span style="font-size: 1.8rem; font-weight: bold; text-align: center; display: block; margin-bottom: 6px;">${kanjiName}</span>${description}`;
    }

    function closeDetail() {
        mainKanjiVideo.pause();
        clearDetailBubbles();
        listPage.style.display = 'flex';
        videoPage.style.display = 'none';

        window.scrollTo(0, savedScrollPosition);
    }

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
                if (!card.classList.contains('special-fuka')) {
                    card.classList.add('active');
                }
                if (video) video.play().catch(e => console.log("Preview play blocked: ", e));
            } else {
                if (!card.classList.contains('special-fuka')) {
                    card.classList.remove('active');
                }
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
