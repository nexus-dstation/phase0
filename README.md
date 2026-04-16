<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>遊技機投資・収益予測プラットフォーム v2 | フェーズ0 目標設定</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700;900&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}

:root{
  --bg:       #07101f;
  --panel:    #0d1b35;
  --gold:     #f5a623;
  --gold-lt:  #ffd080;
  --blue:     #4fc3f7;
  --green:    #4caf81;
  --red:      #ef5350;
  --t1:       #ffffff;
  --t2:       #8fadd4;
  --t3:       #4a6080;
  --br:       rgba(255,255,255,.10);
}

html,body{width:100%;height:100%;overflow:hidden;
  font-family:'Noto Sans JP',sans-serif;
  background:var(--bg);color:var(--t1);}

/* ── スライドシステム ── */
.deck{position:relative;width:100vw;height:100vh;overflow:hidden;}

.slide{
  position:absolute;inset:0;
  display:flex;flex-direction:column;
  background:var(--panel);
  opacity:0;transform:translateX(48px);
  transition:opacity .4s ease,transform .4s ease;
  pointer-events:none;
}
.slide.active{opacity:1;transform:none;pointer-events:all;}
.slide.prev{opacity:0;transform:translateX(-48px);}
.slide::after{
  content:'';position:absolute;top:0;left:0;right:0;height:3px;z-index:10;
  background:linear-gradient(90deg,var(--gold),var(--blue),transparent);
  opacity:.55;
}
.bg-grid{
  position:absolute;inset:0;pointer-events:none;
  background-image:
    linear-gradient(rgba(79,195,247,.025) 1px,transparent 1px),
    linear-gradient(90deg,rgba(79,195,247,.025) 1px,transparent 1px);
  background-size:70px 70px;
}

/* ── ヘッダー ── */
.s-head{padding:28px 56px 0;display:flex;align-items:center;gap:14px;flex-shrink:0;z-index:1;position:relative;}
.s-num{font-size:12px;font-weight:700;color:var(--gold);letter-spacing:2px;}
.s-tag{
  background:rgba(245,166,35,.12);border:1px solid rgba(245,166,35,.3);
  color:var(--gold);font-size:11px;font-weight:700;
  padding:4px 14px;border-radius:20px;letter-spacing:1px;
}

/* ── ボディ ── */
.s-body{
  flex:1;padding:22px 56px 64px;
  display:flex;flex-direction:column;
  overflow:hidden;position:relative;z-index:1;
}
.s-title{
  font-size:36px;font-weight:700;line-height:1.25;
  margin-bottom:28px;
}
.s-title em{font-style:normal;color:var(--gold);}

/* ── カード ── */
.card{
  background:rgba(255,255,255,.05);
  border:1px solid var(--br);border-radius:14px;padding:24px 28px;
}
.card-gold{background:rgba(245,166,35,.08);border-color:rgba(245,166,35,.3);}
.card-blue{background:rgba(79,195,247,.07);border-color:rgba(79,195,247,.28);}
.card-green{background:rgba(76,175,129,.07);border-color:rgba(76,175,129,.28);}
.card-red{background:rgba(239,83,80,.07);border-color:rgba(239,83,80,.25);}

/* ── ナビ ── */
.nav{
  position:fixed;bottom:22px;left:50%;transform:translateX(-50%);
  display:flex;align-items:center;gap:12px;z-index:100;
  background:rgba(7,16,31,.9);padding:9px 20px;
  border-radius:40px;border:1px solid var(--br);backdrop-filter:blur(20px);
}
.nav-btn{
  width:34px;height:34px;border-radius:50%;
  border:1px solid var(--br);background:rgba(255,255,255,.07);
  color:var(--t1);cursor:pointer;font-size:16px;
  display:flex;align-items:center;justify-content:center;transition:all .2s;
}
.nav-btn:hover{background:rgba(245,166,35,.2);border-color:var(--gold);color:var(--gold);}
.nav-dots{display:flex;gap:6px;}
.dot{width:6px;height:6px;border-radius:50%;background:var(--t3);cursor:pointer;transition:all .3s;}
.dot.on{width:18px;border-radius:3px;background:var(--gold);}
.nav-ctr{font-size:12px;color:var(--t2);min-width:36px;text-align:center;}

/* ════════════════════════════════
   SLIDE 1: タイトル
════════════════════════════════ */
#s1{justify-content:center;
  background:linear-gradient(135deg,#060d1f 0%,#0d1b35 55%,#06182c 100%);}
.s1-deco{
  position:absolute;right:5%;top:50%;transform:translateY(-50%);
  font-size:260px;font-weight:900;color:var(--gold);
  opacity:.08;line-height:1;letter-spacing:-14px;pointer-events:none;user-select:none;
}
.s1-glow1{position:absolute;width:700px;height:700px;top:-150px;right:-100px;
  border-radius:50%;background:radial-gradient(circle,rgba(245,166,35,.1),transparent 70%);pointer-events:none;}
.s1-glow2{position:absolute;width:450px;height:450px;bottom:-80px;left:60px;
  border-radius:50%;background:radial-gradient(circle,rgba(79,195,247,.07),transparent 70%);pointer-events:none;}
.s1-inner{position:relative;z-index:1;padding:0 80px;width:100%;}
.s1-label{font-size:13px;font-weight:700;letter-spacing:3px;color:var(--gold);text-transform:uppercase;margin-bottom:22px;}
.s1-main{font-size:72px;font-weight:900;line-height:1.15;margin-bottom:12px;}
.s1-main .hl{background:linear-gradient(90deg,var(--gold),var(--gold-lt));-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.s1-sub{font-size:22px;font-weight:300;color:var(--t2);margin-bottom:44px;}
.s1-bar{width:70px;height:3px;background:linear-gradient(90deg,var(--gold),transparent);margin:32px 0;border-radius:2px;}
.s1-meta{display:flex;gap:32px;}
.s1-m{display:flex;flex-direction:column;gap:5px;}
.s1-ml{font-size:10px;color:var(--t3);letter-spacing:1px;}
.s1-mv{font-size:14px;font-weight:500;color:var(--t2);}

/* ════════════════════════════════
   SLIDE 2: 目標
════════════════════════════════ */
.goal-flow{
  display:flex;align-items:center;gap:0;flex:1;
}
.gf-box{
  flex:1;border-radius:16px;padding:32px;
  display:flex;flex-direction:column;justify-content:center;gap:16px;
}
.gf-step{font-size:11px;font-weight:700;letter-spacing:2px;opacity:.7;}
.gf-title{font-size:32px;font-weight:700;line-height:1.35;}
.gf-body{font-size:16px;color:var(--t2);line-height:1.75;}
.gf-arr{
  display:flex;flex-direction:column;align-items:center;gap:6px;
  padding:0 20px;flex-shrink:0;
}
.gf-arr-icon{font-size:36px;color:var(--gold);opacity:.6;}
.gf-arr-label{font-size:11px;color:var(--t3);}

/* ════════════════════════════════
   SLIDE 3: 何が問題か
════════════════════════════════ */
.prob-list{display:flex;flex-direction:column;gap:16px;flex:1;justify-content:center;}
.prob{
  display:flex;align-items:flex-start;gap:18px;
  padding:20px 24px;
  border-radius:12px;
  border-left:4px solid var(--gold);
}
.prob-ico{font-size:26px;flex-shrink:0;margin-top:2px;}
.prob-h{font-size:20px;font-weight:700;margin-bottom:6px;}
.prob-p{font-size:15px;color:var(--t2);line-height:1.7;}

/* ════════════════════════════════
   SLIDE 4: 解決アプローチ
════════════════════════════════ */
.approach-grid{
  display:grid;grid-template-columns:1fr auto 1fr;
  gap:14px;align-items:center;
}
.ap-box{border-radius:14px;padding:24px;}
.ap-label{font-size:11px;font-weight:700;letter-spacing:2px;margin-bottom:14px;opacity:.75;}
.ap-list{list-style:none;display:flex;flex-direction:column;gap:10px;}
.ap-list li{
  font-size:15px;padding:8px 12px;border-radius:8px;
  display:flex;align-items:center;gap:10px;
}
.ap-list li::before{content:'';width:6px;height:6px;border-radius:50%;flex-shrink:0;}
.ap-indep{background:rgba(79,195,247,.07);border:1px solid rgba(79,195,247,.22);}
.ap-indep .ap-label{color:var(--blue);}
.ap-indep .ap-list li{background:rgba(79,195,247,.05);}
.ap-indep .ap-list li::before{background:var(--blue);}
.ap-dep{background:rgba(245,166,35,.07);border:1px solid rgba(245,166,35,.25);}
.ap-dep .ap-label{color:var(--gold);}
.ap-dep .ap-list li{background:rgba(245,166,35,.05);}
.ap-dep .ap-list li::before{background:var(--gold);}
.ap-arr{display:flex;flex-direction:column;align-items:center;gap:6px;}
.ap-arr-icon{font-size:32px;color:var(--gold);opacity:.6;}
.ap-arr-text{font-size:12px;color:var(--t3);text-align:center;line-height:1.5;}
.source-row{
  background:rgba(255,255,255,.04);border:1px solid var(--br);
  border-radius:12px;padding:18px 24px;
  display:flex;gap:20px;align-items:center;margin-top:16px;
}

/* ════════════════════════════════
   SLIDE 5: 補強データ
════════════════════════════════ */
.magic{display:flex;align-items:stretch;gap:10px;flex:1;}
.mg{
  flex:1;border-radius:14px;padding:22px 16px;
  display:flex;flex-direction:column;gap:10px;
  position:relative;overflow:hidden;
}
.mg::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;}
.mg-n{font-size:52px;font-weight:900;line-height:.9;}
.mg-lbl{font-size:10px;font-weight:700;letter-spacing:1px;opacity:.6;}
.mg-ttl{font-size:16px;font-weight:700;line-height:1.35;}
.mg-desc{font-size:13px;line-height:1.7;opacity:.7;flex:1;}
.mg-bdg{display:inline-block;font-size:11px;font-weight:700;padding:4px 10px;border-radius:20px;align-self:flex-start;}
.mg1{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.09);}
.mg1::before{background:#4a6080;}
.mg1 .mg-n{color:#8fadd4;}
.mg2{background:rgba(245,166,35,.06);border:1px solid rgba(245,166,35,.22);}
.mg2::before{background:var(--gold);}
.mg2 .mg-n{color:var(--gold);}.mg2 .mg-ttl{color:var(--gold-lt);}
.mg3{background:rgba(76,175,129,.07);border:1px solid rgba(76,175,129,.28);}
.mg3::before{background:var(--green);}
.mg3 .mg-n{color:var(--green);}.mg3 .mg-ttl{color:#6de4a8;}
.mg4{background:rgba(79,195,247,.07);border:1px solid rgba(79,195,247,.28);}
.mg4::before{background:var(--blue);}
.mg4 .mg-n{color:var(--blue);}.mg4 .mg-ttl{color:#7ad9ff;}
.impl{
  background:rgba(245,166,35,.07);border:1px solid rgba(245,166,35,.25);
  border-radius:12px;padding:14px 20px;
  display:flex;align-items:center;gap:14px;
  margin-top:14px;flex-shrink:0;
}

@media print{
  html,body{overflow:visible;width:1280px;height:auto;}
  .deck{overflow:visible;height:auto;}
  .slide{position:relative;opacity:1!important;transform:none!important;pointer-events:all!important;page-break-after:always;height:720px;width:1280px;}
  .nav{display:none;}
}
</style>
</head>
<body>
<div class="deck">

<!-- ══════════════════════════════════════
     SLIDE 1 : タイトル
══════════════════════════════════════ -->
<section class="slide active" id="s1">
  <div class="bg-grid"></div>
  <div class="s1-glow1"></div>
  <div class="s1-glow2"></div>
  <div class="s1-deco">v2</div>
  <div class="s1-inner" style="display:flex;flex-direction:column;justify-content:center;height:100%;">
    <div class="s1-label">遊技機投資・収益予測プラットフォーム v2</div>
    <div class="s1-main">
      フェーズ0<br>
      <span class="hl">目標設定</span>
    </div>
    <div class="s1-bar"></div>
    <div class="s1-sub">購入台数に根拠を持たせる — 店舗に合った買い方の構築</div>
    <div class="s1-meta">
      <div class="s1-m"><span class="s1-ml">DATE</span><span class="s1-mv">2026年4月</span></div>
      <div class="s1-m"><span class="s1-ml">PHASE</span><span class="s1-mv">Phase 0 — 目標設定</span></div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     SLIDE 2 : 目標
══════════════════════════════════════ -->
<section class="slide" id="s2">
  <div class="bg-grid"></div>
  <div class="s-head"><span class="s-num">02 / 06</span><span class="s-tag">目標</span></div>
  <div class="s-body">
    <div class="s-title">フェーズ0<em>目標</em></div>

    <div class="goal-flow">
      <!-- GOAL -->
      <div class="gf-box card-gold">
        <div class="gf-step">GOAL</div>
        <div class="gf-title" style="color:var(--gold);">購入台数に<br>根拠を持たせる</div>
        <div class="gf-body">
          いつ・何台・なぜ買うかを<br>
          データで説明できる状態をつくる
        </div>
      </div>

      <!-- 矢印 -->
      <div class="gf-arr">
        <div class="gf-arr-icon">→</div>
        <div class="gf-arr-label">目的</div>
      </div>

      <!-- OUTCOME -->
      <div class="gf-box card-blue">
        <div class="gf-step">OUTCOME</div>
        <div class="gf-title" style="color:var(--blue);">店舗に合った<br>買い方の構築</div>
        <div class="gf-body">
          店舗ごとの客層・回遊特性をもとに<br>
          最適な機種・台数を選定できる体制
        </div>
      </div>
    </div>

    <!-- 補足バー -->
    <div style="margin-top:20px;background:rgba(255,255,255,.04);border:1px solid var(--br);border-radius:12px;padding:18px 24px;display:flex;align-items:center;gap:16px;">
      <span style="font-size:22px;">📌</span>
      <p style="font-size:16px;color:var(--t2);line-height:1.65;">
        「良い台を増やす」より「<strong style="color:var(--gold);">悪い台を買い過ぎない</strong>」。機種の良し悪しより、<strong style="color:var(--t1);">台数の判断に根拠</strong>を持たせることが先決。
      </p>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     SLIDE 3 : 何が問題か
══════════════════════════════════════ -->
<section class="slide" id="s3">
  <div class="bg-grid"></div>
  <div class="s-head"><span class="s-num">03 / 06</span><span class="s-tag">問題の構造</span></div>
  <div class="s-body">
    <div class="s-title">なぜ<em>根拠がない</em>買い方になるのか</div>

    <div class="prob-list">
      <div class="prob card">
        <div class="prob-ico">📊</div>
        <div>
          <div class="prob-h">担当者任せで予測する仕組みがない</div>
          <div class="prob-p">機種ごとの投資効率を事前に推定する手段がなく、導入台数は担当者の経験・感覚・メーカー提案に依存している。</div>
        </div>
      </div>
      <div class="prob card">
        <div class="prob-ico">🏪</div>
        <div>
          <div class="prob-h">店舗ごとの特性が見えていない</div>
          <div class="prob-p">同じ機種でも、店舗の客層・既存台構成・回遊パターンによって結果は大きく変わる。しかし現状は全店ほぼ同一判断になりやすい。</div>
        </div>
      </div>
      <div class="prob card">
        <div class="prob-ico">🔄</div>
        <div>
          <div class="prob-h">機種間の「つながり」で評価できていない</div>
          <div class="prob-p">新台が既存の台群の中で「選択肢の一部」として機能するかどうかを見ていない。単体評価だけでは判断を誤る。</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     SLIDE 4 : 解決アプローチ
══════════════════════════════════════ -->
<section class="slide" id="s4">
  <div class="bg-grid"></div>
  <div class="s-head"><span class="s-num">04 / 06</span><span class="s-tag">解決アプローチ</span></div>
  <div class="s-body">
    <div class="s-title"><em>新台回遊データ</em>を軸に、根拠をつくる</div>

    <div class="approach-grid" style="flex:1;">
      <!-- 説明変数 -->
      <div class="ap-box ap-indep">
        <div class="ap-label">説明変数（導入前に取得可能）</div>
        <ul class="ap-list">
          <li>🎭 版権</li>
          <li>⚙️ スペック</li>
          <li>🏭 メーカー</li>
          <li>📍 配置</li>
          <li>📅 導入時期</li>
        </ul>
      </div>

      <!-- 矢印 -->
      <div class="ap-arr">
        <div class="ap-arr-icon">⇒</div>
        <div class="ap-arr-text">影響度<br>分析</div>
      </div>

      <!-- 目的変数 -->
      <div class="ap-box ap-dep">
        <div class="ap-label">目的変数</div>
        <ul class="ap-list">
          <li>🔄 店舗ごとの新台回遊データ</li>
        </ul>
        <div style="margin-top:18px;font-size:15px;color:var(--t2);line-height:1.75;">
          顧客が複数機種を移動する「回遊行動」を定着の指標に設定。<br>
          どの特性が回遊に最も影響するかを抽出し、<br>
          <strong style="color:var(--gold);">「売れやすい背景」を定量化する。</strong>
        </div>
      </div>
    </div>

    <!-- ソース -->
    <div class="source-row">
      <div style="flex-shrink:0;">
        <div style="font-size:14px;font-weight:700;">THINX · 吉元氏</div>
        <div style="font-size:13px;color:var(--t2);">上場メーカー遊技機開発/ データアナリスト・統計士</div>
      </div>
      <div style="width:1px;background:var(--br);align-self:stretch;"></div>
      <div style="font-size:14px;color:var(--t2);line-height:1.75;flex:1;">
        「重要なのは回遊データを起点に、導入前の説明変数と目的変数の関係を可視化することだ」
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     SLIDE 5 : 補強データ
══════════════════════════════════════ -->
<section class="slide" id="s5">
  <div class="bg-grid"></div>
  <div class="s-head"><span class="s-num">05 / 06</span><span class="s-tag">補強データ</span></div>
  <div class="s-body">
    <div class="s-title"><em>複数体験</em>が定着を生む構造（THINX-LAB 分析）</div>

    <div class="magic">
      <div class="mg mg1">
        <div class="mg-n">1</div>
        <div class="mg-lbl">機種体験</div>
        <div class="mg-ttl">評価固定・<br>離反リスク高</div>
        <div class="mg-desc">単一機種のみの顧客は評価が固定され、結果次第で離反に直結しやすい。</div>
        <div class="mg-bdg" style="background:rgba(255,255,255,.06);color:var(--t3);border:1px solid rgba(255,255,255,.1);">高リスク</div>
      </div>
      <div class="mg mg2">
        <div class="mg-n">2</div>
        <div class="mg-lbl">機種体験</div>
        <div class="mg-ttl">比較が生まれ<br>行動が変化</div>
        <div class="mg-desc">比較行動が発生し、特定機種への依存度が下がる。選好の探索が始まる。</div>
        <div class="mg-bdg" style="background:rgba(245,166,35,.12);color:var(--gold);border:1px solid rgba(245,166,35,.25);">変化の境界</div>
      </div>
      <div class="mg mg3">
        <div class="mg-n">4</div>
        <div class="mg-lbl">機種体験</div>
        <div class="mg-ttl">探索が習慣化<br>定着率急上昇</div>
        <div class="mg-desc">来店目的が「特定台を打つ」から「選んで遊ぶ」へ変質。定着の段差が生まれる。</div>
        <div class="mg-bdg" style="background:rgba(76,175,129,.12);color:var(--green);border:1px solid rgba(76,175,129,.25);">定着ライン</div>
      </div>
      <div class="mg mg4">
        <div class="mg-n">∞</div>
        <div class="mg-lbl">複数選択肢</div>
        <div class="mg-ttl">離反しにくい<br>顧客構造の完成</div>
        <div class="mg-desc">複数機種遊技者は単一遊技者より明確に離反しにくい。選択肢の豊かさが顧客定着を支える。</div>
        <div class="mg-bdg" style="background:rgba(79,195,247,.12);color:var(--blue);border:1px solid rgba(79,195,247,.25);">目標状態</div>
      </div>
    </div>

    <div class="impl">
      <span style="font-size:20px;">💡</span>
      <div style="font-size:15px;font-weight:500;line-height:1.65;">
        <strong style="color:var(--gold);">新台導入への示唆：</strong>
        新台は「単体の出玉評価」ではなく「<strong>既存の台群の中で選択肢として機能するか</strong>」で評価すべき。これが回遊モデルを根拠に使う理由。
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     SLIDE 6 : まとめ
══════════════════════════════════════ -->
<section class="slide" id="s6">
  <div class="bg-grid"></div>
  <div class="s-head"><span class="s-num">06 / 06</span><span class="s-tag">まとめ</span></div>
  <div class="s-body">
    <div class="s-title">まとめ：実務上の難易度と<em>解決の方向性</em></div>

    <div style="display:flex;flex-direction:column;gap:18px;flex:1;">
      
      <!-- 結論1 -->
      <div class="card card-red" style="padding:22px 28px;">
        <span style="font-weight:700;color:var(--red);font-size:18px;margin-bottom:10px;display:block;">完全な個別最適化は、実務上困難である</span>
        <p style="font-size:16px;color:var(--t2);line-height:1.75;">
          「店舗ごとの特性と掛け合わせた購入判断」は一定の精度で選択の幅を狭めます。しかし基本的に、顧客の嗜好性は<span style="color:var(--t1);font-weight:700;">店舗規模の大小に関わらず、マクロとミクロで同様の性質を持つ傾向</span>があります。<br>
          したがって、「無理なく（買いすぎない）・無駄なく（不足なく）」という観点で、各店舗ごとに最適化された購入判断を構築することは、実務上は難易度が高い領域になります。
        </p>
      </div>

      <!-- 結論2 -->
      <div class="card card-blue" style="padding:22px 28px;">
        <span style="font-weight:700;color:var(--blue);font-size:18px;margin-bottom:10px;display:block;">機種の必要性には「再現性」がある</span>
        <p style="font-size:16px;color:var(--t2);line-height:1.75;">
          言い換えると、店舗規模の大小に関わらず、<span style="color:var(--t1);font-weight:700;">必要とされる機種は一定の再現性をもって“必要になる”構造</span>にあると考えられます。
        </p>
      </div>

      <!-- 結論3 -->
      <div class="card card-gold" style="padding:26px 28px;border-left:8px solid var(--gold);flex:1;display:flex;align-items:center;">
        <div style="display:flex;align-items:flex-start;gap:18px;">
          <span style="font-size:36px;line-height:1;">🎯</span>
          <div>
            <span style="font-weight:700;color:var(--gold);font-size:22px;margin-bottom:12px;display:block;">目指すべきアプローチ</span>
            <p style="font-size:18px;color:var(--t1);line-height:1.7;font-weight:500;">
              導入前に取得できる「明確な説明変数」を設置し、<br>
              どの要素が「回遊（目的変数）」に最も影響しているかを抽出する。
            </p>
          </div>
        </div>
      </div>
      
    </div>
  </div>
</section>

</div><!-- /deck -->

<!-- ナビゲーション -->
<nav class="nav">
  <button class="nav-btn" onclick="go(-1)">‹</button>
  <div class="nav-dots" id="dots"></div>
  <span class="nav-ctr" id="ctr">1 / 6</span>
  <button class="nav-btn" onclick="go(1)">›</button>
</nav>

<script>
const N=6;let cur=1;
const dotsEl=document.getElementById('dots');
for(let i=1;i<=N;i++){
  const d=document.createElement('div');
  d.className='dot'+(i===1?' on':'');
  d.onclick=()=>goTo(i);
  dotsEl.appendChild(d);
}
function goTo(n){
  const prev=document.getElementById('s'+cur);
  prev.classList.remove('active');prev.classList.add('prev');
  setTimeout(()=>prev.classList.remove('prev'),450);
  cur=Math.max(1,Math.min(n,N));
  document.getElementById('s'+cur).classList.add('active');
  document.getElementById('ctr').textContent=cur+' / '+N;
  document.querySelectorAll('.dot').forEach((d,i)=>d.classList.toggle('on',i+1===cur));
}
function go(d){goTo(cur+d);}
document.addEventListener('keydown',e=>{
  if(e.key==='ArrowRight'||e.key==='ArrowDown')go(1);
  if(e.key==='ArrowLeft'||e.key==='ArrowUp')go(-1);
});
</script>
</body>
</html>
