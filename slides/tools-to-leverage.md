---
layout: default
---

# 手間を肩代わりしてくれるツール

<div class="text-base opacity-70 mt-2">
  レイヤー構造 — それぞれが他のツールでは見逃すものを拾う。
</div>

<div class="grid grid-cols-3 gap-4 mt-8">

<div class="rounded-lg border border-gray-700 p-4">
  <div class="flex items-center gap-2 mb-2">
    <logos-eslint class="text-2xl" />
    <span class="font-semibold">ESLint プラグイン</span>
  </div>
  <div class="text-sm opacity-80 leading-relaxed">
    <em>書いている最中に</em> 問題を検出。alt 不足、不適切な ARIA、ラベルのないコントロールなど。
  </div>
  <div class="text-xs opacity-50 mt-2 font-mono">
    eslint-plugin-jsx-a11y · eslint-plugin-vuejs-accessibility
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-4">
  <div class="flex items-center gap-2 mb-2">
    <lucide-scan-eye class="text-2xl text-pink-400" />
    <span class="font-semibold">axe DevTools</span>
  </div>
  <div class="text-sm opacity-80 leading-relaxed">
    無料のブラウザ拡張。レンダリング後のページをスキャン。WCAG 課題の平均約 57%* を検出。
  </div>
  <div class="text-xs opacity-50 mt-2">
    * Deque による 2021 年の調査(13,000 ページ・約 30 万件の課題)
  </div>
  <div class="text-xs opacity-50 mt-2">
    <a href="https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd" target="_blank">
      Chrome 拡張をインストール
    </a>
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-4">
  <div class="flex items-center gap-2 mb-2">
    <logos-chrome class="text-2xl" />
    <span class="font-semibold">Lighthouse</span>
  </div>
  <div class="text-sm opacity-80 leading-relaxed">
    Chrome DevTools に標準搭載。アクセシビリティ + SEO + パフォーマンスを一度に。内部では axe-core を使用。
  </div>
  <div class="text-xs opacity-50 mt-2">
    DevTools → Lighthouse タブ
  </div>
</div>

</div>

<div v-click class="mt-8 text-sm opacity-60 text-center">
  おまけ: <a href="https://storybook.js.org/addons/@storybook/addon-a11y" target="_blank"><strong>Storybook a11y addon</strong></a> — 同じ axe エンジン、コンポーネント単位で実行。
</div>

---
layout: default
transition: slide-up
---

# 何も言わないラベル

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> ツールがチェックすること
  </div>

  <div class="text-sm opacity-70 mb-3">ルール: 操作可能な要素にはアクセシブルな名前が必須。</div>

```html
<button aria-label="button">
  <lucide-search />
</button>

<img src="chart.png" alt="image" />
```

  <div class="text-xs opacity-60 mt-3">
    名前が存在する → 監査をパス。
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> 実際に起きていること
  </div>

<div class="rounded-lg border border-gray-700 p-4 mt-2 bg-gray-900 font-mono text-sm">
  <div class="opacity-60">スクリーンリーダーの読み上げ:</div>
  <div class="mt-2"><lucide-volume-2 class="inline text-pink-400" /> 「ボタン、ボタン」</div>
  <div class="mt-1"><lucide-volume-2 class="inline text-pink-400" /> 「画像、画像」</div>
</div>

  <div class="text-xs opacity-60 mt-3">
    ユーザーには、ボタンの <em>役割</em> も、画像の <em>内容</em> もわからない。
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  ラベルは <strong>そのものを説明している時にだけ</strong> 役に立つ。
</div>

---
layout: default
transition: slide-up
---

# プレースホルダーはラベルではない

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> ツールがチェックすること
  </div>

  <div class="text-sm opacity-70 mb-3">ルール: <em>何らかの</em> ソースからアクセシブルな名前を取得できる。</div>

```html
<input
  type="text"
  placeholder="IBAN: 例 BE71 0961 2345 6769"
/>
```

  <div class="text-xs opacity-60 mt-3">
    プレースホルダーが名前として認識される → パス(設定による)。
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> 実際に起きていること
  </div>

  <PlaceholderDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    入力を始めた瞬間に「ラベル」が消える。
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  ラベルは残る。プレースホルダーは <strong>ヒント</strong> であって、ラベルではない。
</div>

---
layout: default
transition: slide-up
---

# 色だけが意味を持つ

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> ツールがチェックすること
  </div>

  <div class="text-sm opacity-70 mb-3">ルール: 必須状態が ARIA またはネイティブ属性で表現されている。</div>

```html
<input
  type="text"
  aria-required="true"
  class="form-input"
/>
```

```css
.form-input:required {
  border-color: red;
}
```

  <div class="text-xs opacity-60 mt-3">
    マークアップに状態が存在する → 監査をパス。
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> 実際に起きていること
  </div>

  <ColorOnlyDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    色覚特性やグレースケールでは全てのフィールドが同じに見える — どれが必須かわからない。
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  色は <em>2番目の</em> シグナル。<strong>1番目のシグナル</strong> が別に必要。
</div>

---
layout: default
---

# フォーカスはどこへ?

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> ツールがチェックすること
  </div>

  <div class="text-sm opacity-70 mb-3">ルール: <code>:focus</code> のスタイルが定義されている。</div>

```css
.btn:focus {
  outline: none;
}

/* または "リセット" CSS */
button {
  outline: 0;
}
```

  <div class="text-xs opacity-60 mt-3">
    CSS ルールが存在する → 監査をパス。
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> 実際に起きていること
  </div>

  <FocusDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    Tab で移動してみよう — キーボードユーザーは自分の位置が <em>全くわからない</em>。
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  フォーカスはキーボードユーザーの <strong>カーソル</strong> だ。
</div>

---
layout: default
---

# スターターチェックリスト

<div class="text-base opacity-70 text-sm">
  最初から全てのルールを覚える必要はない。これらを意識しつつ、迷ったらツールに頼ろう。
</div>

<Checklist />