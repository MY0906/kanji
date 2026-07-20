<style>
    /* 1. GitHub Pagesが自動生成する上部ヘッダーやタイトル、余計な枠をページ全体から完全に消滅させる */
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

    /* 2. GitHubが強制的にかけてくるページの余白や外枠（スクロール制限など）をすべてリセットする */
    html, body, .markdown-body {
        margin: 0 !important;
        padding: 0 !important;
        background-color: #f7f9fa !important;
        font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', sans-serif;
        overflow-x: hidden;
        max-width: 100% !important;
        box-shadow: none !important;
    }

    /* 一覧画面（画面の最上部から綺麗にサムネイルが敷き詰められます） */
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

    /* 漢字ボタンのコンテナ（動画サムネイル） */
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

    /* サムネイル動画 */
    .kanji-video-thumb {
        width: 100%;
        height: 100%;
        object-fit: contain;
        user-select: none;
    }

    /* 3. 詳細画面（最前面（z-index: 999999）に引き上げて、GitHubのいかなる要素とも干渉させない） */
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
        z-index: 999999 !important; /* 絶対に他のものに邪魔させない最高値 */
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

<div id="list-page">
    <div class="kanji-thumb-container" onclick="openDetail('雨', '空から水滴が
    
