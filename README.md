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

    /* 縦一列のレイアウト */
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

    /* 漢字カード本体 */
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
        transform: scale(1.01);
        box-shadow: 0 12px 32px rgba(0,0,0,0.1);
    }

    /* 動画を表示するエリア（タップイベントを完全に貫通させる） */
    .video-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        border-radius: 16px;
        overflow: hidden;
        background-color: #ffffff;
        position: relative;
        pointer-events: none; /* 【重要】ここにあるすべてのタップを貫通させて下のカードに届ける */
    }

    .kanji-video {
        width: 100%;
        height: 100%;
        object-fit: contain;
        -webkit-user-select: none;
        user-select: none;
    }

    /* 初期状態では説明文エリアを非表示にする */
    .kanji-info {
        max-height: 0;
        opacity: 0;
        overflow: hidden;
        transition: max-height 0.4s ease, opacity 0.4s ease, margin-top 0.3s ease;
        text-align: center;
        width: 100%;
    }

    /* カードをタップして「show-desc」クラスがついたら表示する */
    .kanji-card.show-desc .kanji-info {
        max-height: 300px;
        opacity: 1;
        margin-top: 25px;
    }

    .kanji-title {
        font-size: 2.2rem;
        font-weight: bold;
        color: #333333;
        margin-bottom: 12px;
    }

    .kanji-text {
        font-size: 1.3rem;
        color: #555555;
        line-height: 1.6;
        word-wrap: break-word;
    }
</style>

<!-- 一覧画面（タップで説明が出る仕組み） -->
<div id="list-page">
    
    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="雨.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">雨</div>
            <div class="kanji-text">空から水滴がぽつぽつと降ってくる様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="羽.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">羽</div>
            <div class="kanji-text">鳥のふさふさとしたはねが並んでいる様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="寒.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">寒</div>
            <div class="kanji-text">家の中で人がわらの中にくるまって、凍えている様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="叫.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">叫</div>
            <div class="kanji-text">口を大きく開けて、大きな声を張り上げてさけぶ様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="月.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">月</div>
            <div class="kanji-text">夜空に浮かぶ美しい三日月の形からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="糸.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">糸</div>
            <div class="kanji-text">細い糸を何本かつむいで、束ねた形からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="集.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">集</div>
            <div class="kanji-text">木の上にたくさんの鳥が集まって止まっている様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-wrapper">
                <video class="kanji-video" src="暑.mp4" playsinline muted loop preload="metadata"></video>
            </video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">暑</div>
            <div class="kanji-text">太陽（日）が照りつけて、お墓の上の人もうだるほどあつい様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="明.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">明</div>
            <div class="kanji-text">太陽（日）と月が合わさって、辺りが明るく照らされている様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="木.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">木</div>
            <div class="kanji-text">大地にしっかりと根を張り、枝を広げた一本の木の形からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="目.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">目</div>
            <div class="kanji-text">人間の目の形（ひとみとまぶた）を縦にした形からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="嵐.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">嵐</div>
            <div class="kanji-text">山の上を激しい風と雨が吹き荒れる様子からできた漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="林.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">林</div>
            <div class="kanji-text">木が２本並んで、木がたくさん生えている場所を表す漢字です。</div>
        </div>
    </div>

    <div class="kanji-card" onclick="toggleDescription(this)">
        <div class="video-wrapper">
            <video class="kanji-video" src="眩.mp4" playsinline muted loop preload="metadata"></video>
        </div>
        <div class="kanji-info">
            <div class="kanji-title">眩</div>
            <div class="kanji-text">目（目）に光が強く差し込んで、クラクラとまぶしい様子からできた漢字です。</div>
        </div>
    </div>

</div>

<script>
    // タップしたときに説明文を出したり消したりする関数
    function toggleDescription(card) {
        card.classList.toggle('show-desc');
    }

    // iPadのスクロールに合わせて動画を自動再生・停止する設定
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
                    video.play().catch(e => console.log("Play blocked: ", e));
                } else {
                    card.classList.remove('active');
                    card.classList.remove('show-desc');
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
