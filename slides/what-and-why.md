---
layout: default
---

# アクセシビリティとは？

能力・デバイス・状況に関わらず、<strong>誰もが</strong>使えるデジタルプロダクトを作ること。

<div class="mt-12 text-2xl italic opacity-80">

> 「Webの力はその<span v-mark.underline.cyan>普遍性</span>にある。
> 障害の有無に関わらず、誰もがアクセスできることが本質的な側面だ。」

</div>

<div class="mt-4 text-right text-sm opacity-60">

— Tim Berners-Lee, World Wide Web の発明者

</div>

<v-clicks at="2">

- 後から追加する機能ではない
- チェックリストで済ませるものでもない
- パフォーマンスやセキュリティと同じ、プロダクトの<span v-mark.circle.pink>品質</span>

</v-clicks>

---
layout: default
---

# グレースケールテスト

同じ UI でも、見え方は人によって違う。

<GrayscaleDemo class="mt-12" />

---
layout: default
---

# WCAG — ルールブック

**Web Content Accessibility Guidelines** — W3C が策定する、デジタルアクセシビリティの国際標準。

<div class="mt-8 text-sm opacity-70">
  4つの原則で構成されていて、頭文字を取って <strong>POUR</strong> と呼ばれる：
</div>

<div class="grid grid-cols-4 gap-3 mt-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">P</div>
    <div class="text-sm font-semibold mt-1">Perceivable<br/>知覚可能</div>
    <div class="text-xs opacity-60 mt-1">コンテンツを認識できる</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">O</div>
    <div class="text-sm font-semibold mt-1">Operable<br/>操作可能</div>
    <div class="text-xs opacity-60 mt-1">操作できる</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">U</div>
    <div class="text-sm font-semibold mt-1">Understandable<br/>理解可能</div>
    <div class="text-xs opacity-60 mt-1">内容や UI が理解できる</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">R</div>
    <div class="text-sm font-semibold mt-1">Robust<br/>堅牢性</div>
    <div class="text-xs opacity-60 mt-1">支援技術と一緒に動作する</div>
  </div>
</div>

<div class="mt-10 text-sm opacity-70">
  3段階の適合レベル(厳しい順):
</div>

<div class="grid grid-cols-3 gap-3 mt-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-xl font-bold text-purple-400">A</div>
    <div class="text-sm opacity-80 mt-1">最低限</div>
    <div class="text-xs opacity-50 mt-1">満たさないと、多くのユーザーにとって使えない</div>
  </div>
  <div class="rounded-lg border-2 border-pink-400 px-4 py-3">
    <div class="text-xl font-bold text-pink-400">AA</div>
    <div class="text-sm opacity-80 mt-1">実務上の標準</div>
    <div class="text-xs opacity-50 mt-1">多くのプロジェクト・法律・ツールが目指すレベル</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-xl font-bold text-purple-400">AAA</div>
    <div class="text-sm opacity-80 mt-1">最高水準</div>
    <div class="text-xs opacity-50 mt-1">全体への適用は稀で、特定の文脈向け</div>
  </div>
</div>

<div class="mt-6 text-xs opacity-50 text-center">
  <a href="https://web.dev/learn/accessibility/measure?hl=ja#wcag" target="_blank">
    <carbon-link class="inline" /> web.dev — Learn Accessibility · WCAG
  </a>
</div>

---
layout: default
transition: slide-up
---

# 色とコントラスト

WCAG AA — ほとんどのプロジェクトが目指すレベル。

<div class="grid grid-cols-2 gap-8 mt-8">

<div class="rounded-lg p-6 border border-gray-600">
  <div class="text-5xl font-bold text-pink-400">4.5:1</div>
  <div class="mt-2 opacity-80">本文テキスト</div>
  <div class="mt-1 text-sm opacity-50">18pt 未満、または太字 14pt 未満</div>
</div>

<div class="rounded-lg p-6 border border-gray-600">
  <div class="text-5xl font-bold text-pink-400">3:1</div>
  <div class="mt-2 opacity-80">大きいテキスト & UI 要素</div>
  <div class="mt-1 text-sm opacity-50">18pt 以上 / 太字 14pt 以上、アイコン、枠線など</div>
</div>

</div>

<ContrastDemo class="mt-10" />

<div class="mt-6 text-sm opacity-60">

DevTools → 要素を検証 → カラーピッカーにコントラスト比が表示される

</div>

---

# その数字の理由

<div class="text-sm opacity-60" style="view-transition-name: ratio-aa"/>

<ContrastVisionDemo />

---
layout: default
---

# ユーザーの裏にある数字

<div class="mt-6">

<div class="text-sm opacity-60 mb-3">色覚特性の種類別 — 男性のうちの割合:</div>

<div class="grid grid-cols-4 gap-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~5%</div>
    <div class="text-sm opacity-80 mt-1">2型3色覚</div>
    <div class="text-xs opacity-50">緑の感度が低下</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~1.2%</div>
    <div class="text-sm opacity-80 mt-1">2型2色覚</div>
    <div class="text-xs opacity-50">緑の錐体細胞なし</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~1%</div>
    <div class="text-sm opacity-80 mt-1">1型3色覚 / 1型2色覚</div>
    <div class="text-xs opacity-50">赤の感度低下 / 赤の錐体細胞なし</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">&lt;0.01%</div>
    <div class="text-sm opacity-80 mt-1">3型2色覚 / 全色盲</div>
    <div class="text-xs opacity-50">青黄色覚 / 完全な色覚なし</div>
  </div>
</div>

</div>

<div v-click class="mt-10 text-center text-lg opacity-70">
  世界全体で合計すると —
</div>

<div class="grid grid-cols-3 gap-8 mt-6">

<div v-click class="text-center">
  <div class="text-5xl font-bold text-pink-400">12人に1人</div>
  <div class="mt-2 text-base opacity-80">の男性が</div>
  <div class="text-base opacity-80">色覚特性を持つ</div>
</div>

<div v-click class="text-center">
  <div class="text-6xl font-bold text-pink-400">13億人</div>
  <div class="mt-2 text-base opacity-80">が何らかの</div>
  <div class="text-base opacity-80">障害と共に生きている</div>
</div>

<div v-click class="text-center" v-mark.circle.pink>
  <div class="text-6xl font-bold text-pink-400">16%</div>
  <div class="mt-2 text-base opacity-80">世界人口の —</div>
  <div class="text-base opacity-80">およそ6人に1人</div>
</div>

</div>

<div v-click class="mt-10 text-center text-lg opacity-80">
  これらは特殊なケースではない。すべてのチームのユーザーの、無視できない割合だ。
</div>

<div v-click class="mt-2 text-center text-xs opacity-40">
  出典: Colour Blind Awareness · WHO Global Report on Disability (2023)
</div>

---
layout: default
---

# 色だけに頼らない

<ColorAloneDemo class="mt-8" />

<div v-click class="mt-8 text-center text-lg opacity-80" click="1">
  色 <strong>と一緒に</strong>、形やアイコンも意味を伝える助けになる
</div>

---
layout: default
---

# 色だけの話じゃない

<div class="mt-6 text-lg opacity-80">
  同じニーズでも、原因はさまざま。
</div>

<div class="grid grid-cols-3 gap-3 mt-6">

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">恒久的</div>
    <div class="text-3xl mb-2"><lucide-hand class="inline" /></div>
    <div class="text-sm">片腕しかない</div>
  </div>

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">一時的</div>
    <div class="text-3xl mb-2"><lucide-bandage class="inline" /></div>
    <div class="text-sm">腕にギプス</div>
  </div>

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">状況的</div>
    <div class="text-3xl mb-2"><lucide-baby class="inline" /></div>
    <div class="text-sm">赤ちゃんを抱っこ中</div>
  </div>

</div>

<div v-click class="mt-8 text-center text-base opacity-70">
  どれも片手操作が必要。アクセシビリティ対応は、この3つすべてに効く。
</div>

<div v-click class="mt-10">

<div class="text-sm opacity-60 mb-3">全体像 — 4種類の特性 × それぞれ3段階の恒久性:</div>

<div class="grid grid-cols-4 gap-2 text-sm">
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">視覚</div>
    <div class="text-xs opacity-60">全盲 · 弱視 · 色覚特性</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">運動</div>
    <div class="text-xs opacity-60">麻痺 · 震え · RSI</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">認知</div>
    <div class="text-xs opacity-60">ディスレクシア · ADHD · 記憶</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">聴覚</div>
    <div class="text-xs opacity-60">ろう · 難聴</div>
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-lg">
  「平均」ではなく、<span v-mark.circle.pink>多様性</span> に合わせて作ろう。
</div>

---
layout: default
---

# 今こそ重要な理由

<div class="grid grid-cols-3 gap-6 mt-8">

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-users /></div>
  <div class="font-semibold text-lg mb-2">人口構成の変化</div>
  <div class="text-sm opacity-80 leading-relaxed">
    高齢化が進行中 — <strong>日本の65歳以上は約29%</strong>(2025年、過去最高)。加齢とともに視力低下・運動機能の衰え・認知負荷が増える。
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    「平均的なユーザー」は、いわゆるアクセシビリティ機能を必要とする方向にシフトしている。
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-smartphone /></div>
  <div class="font-semibold text-lg mb-2">モバイルと利用環境</div>
  <div class="text-sm opacity-80 leading-relaxed">
    スマホは、誰にとっても一時的な制約をもたらす — 屋外の眩しさ、電車での片手操作、騒がしいカフェ、小さなタップ領域。
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    ユーザーは <em>すでに</em> アクセシビリティの壁にぶつかっている。そう呼んでいないだけ。
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-trending-up /></div>
  <div class="font-semibold text-lg mb-2">SEO と開発上のメリット</div>
  <div class="text-sm opacity-80 leading-relaxed">
    セマンティック HTML、alt テキスト、見出し階層、ARIA — Google はこれら全てをランキングのシグナルとして読む。
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    同じ手間で、二度おいしい: <strong>Lighthouse スコアの向上</strong> と <strong>よりアクセシブルなプロダクト</strong>。
  </div>
</div>

</div>