---
layout: default
---

# セマンティック HTML が仕事の8割

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> 自前で実装
  </div>

```html
<div class="btn" onclick="submit()">
    Submit
</div>
```

</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> ネイティブ
  </div>

```html
<button type="submit">
    Submit
</button>
```

</div>

</div>

<div class="mt-6">

| 機能                         | `<div onclick>` | `<button>` |
|----------------------------|:---------------:|:----------:|
| キーボードフォーカス可能               |        ❌        |     ✅      |
| Enter / Space で発火          |        ❌        |     ✅      |
| スクリーンリーダーに「ボタン」と認識される      |        ❌        |     ✅      |
| 無効化状態 (`:disabled` で発火しない) |        ❌        |     ✅      |

</div>

<div class="mt-6 text-center text-base opacity-80">
  自前で実装するなら、これらすべてのサポートは <span v-mark.underline.pink>自分の責任</span>
</div>

---
layout: default
---

# キーボードファースト

<div class="text-lg opacity-80 mt-2">
  パワーユーザーも、エンジニアもここで生きている。ユーザーだって同じはず。
</div>

<div class="grid grid-cols-2 gap-8 mt-8">

<div>
  <KeyboardDemo />
</div>

<div>

```html
<dialog>
    <form method="dialog">
        <h2>配送オプション</h2>

        <fieldset>
            <legend>速度</legend>
            <label><input type="radio" name="speed"/> 通常</label>
            <label><input type="radio" name="speed"/> 速達</label>
            <label><input type="radio" name="speed"/> 翌日配送</label>
        </fieldset>

        <button>キャンセル</button>
        <button>確定</button>
    </form>
</dialog>
```

</div>

</div>

<div class="mt-6 grid grid-cols-4 gap-3 text-sm">
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Tab</kbd> — フィールド/ボタン間を移動
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>↑</kbd> <kbd>↓</kbd> — ラジオボタンを選択
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Enter</kbd> — 実行 / 送信
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Esc</kbd> — ダイアログを閉じる
  </div>
</div>

<div v-click class="mt-6 text-center text-sm opacity-70">
  <code>&lt;dialog&gt;</code> は <a href="LINK_TO_FEBI_CSS_DECK" target="_blank" class="underline">前回のスライド</a> で詳しく取り上げた。
  これらすべてがネイティブ機能で、JS のキーボード処理は一切不要。
</div>

---
layout: default
---

# ラベルと名前

<div class="text-lg opacity-80 mt-2">
  操作可能な要素には、スクリーンリーダーが読み上げられる名前が必要。
</div>

<div class="mt-6 grid grid-cols-[10rem_1fr_1fr] gap-x-4 gap-y-6 items-start text-sm">

<div class="text-xs uppercase tracking-wider opacity-50 self-center">入力フィールド</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> <code>&lt;label&gt;</code> がない — スクリーンリーダーが読み上げられない</div>

```html
<input type="email"/>
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>&lt;label for&gt;</code> でテキストと入力フィールドを紐づける</div>

```html
<label for="email">Email</label>
<input id="email" type="email"/>
```

</div>

<div class="text-xs uppercase tracking-wider opacity-50 self-center">アイコンボタン</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> アイコンだけ — 目的のない「ボタン」として読まれる</div>

```html
<button>
    <lucide-x/>
</button>
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>aria-label</code> で欠けている名前を補う</div>

```html
<button aria-label="ダイアログを閉じる">
    <lucide-x/>
</button>
```

</div>

<div class="text-xs uppercase tracking-wider opacity-50 self-center">フォームエラー</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> エラーが紐づかない — 文脈なしで読まれる</div>

```html
<input id="email" aria-invalid="true"/>
<p>有効なメールアドレスを入力してください。</p>
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>aria-describedby</code> でエラーと入力を結びつける</div>

```html
<input 
  id="email" 
  aria-invalid="true" 
  aria-describedby="email-err"
/>
<p id="email-err">有効なメールアドレスを入力してください。</p>
```

</div>

</div>

---
layout: default
---

# 実際に聞いてみよう <carbon-volume-up class="inline" />

<div class="text-sm opacity-60 mt-1">
  Cmd+F5 で VoiceOver をオン — Tab で両側を移動してみよう。
</div>

<LabelsDemo class="mt-6" />

---
layout: default
---

# ARIA — 慎重に扱うべきもの

<blockquote class="mt-4 pl-4 border-l-4 border-pink-400">
  <div class="text-base italic">「ARIA の第一のルール: ARIA を使わないこと」</div>
  <div class="mt-1 text-xs opacity-50">— W3C, ARIA Authoring Practices</div>
</blockquote>

<div class="grid grid-cols-2 gap-6 mt-6 text-sm">

<!-- DON'T column -->
<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-3"><lucide-x class="inline" /> やってはいけない</div>

  <div class="don-block">
    <div class="don-label">冗長 — <code>&lt;button&gt;</code> はすでに role を持っている</div>

```html
<button role="button">保存</button>
```

  </div>

<div class="don-block">
  <div class="don-label">ネイティブの再実装 — Tab と Space を試してみよう</div>

  <CustomCheckboxDemo class="mt-2" />
</div>

<div class="don-block">
  <div class="don-label">ゴーストサブツリー — フォーカス可能な子要素が沈黙する</div>

```html
<div aria-hidden="true">
    <h2>装飾セクション</h2>
    <button>もっと読む</button>
</div>
```

</div>
</div>

<!-- DO column -->
<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-3"><lucide-check class="inline" /> やるべきこと</div>

  <div class="do-block">
    <div class="do-label">アイコンだけのボタンに名前をつける</div>

```html
<button aria-label="ダイアログを閉じる">
    <lucide-x/>
</button>
```

  </div>

  <div class="do-block">
    <div class="do-label">動的な更新をアナウンスする</div>

```html
<div aria-live="polite" role="status">
    保存しました。
</div>
```

  </div>

  <div class="do-block">
    <div class="do-label">トグルの状態を伝える</div>

```html
<button aria-expanded="false" aria-controls="menu">
    メニュー
</button>
```

  </div>
</div>

</div>

<style scoped>
.don-block, .do-block {
  margin-bottom: 1rem;
}

.don-label, .do-label {
  font-size: 0.75rem;
  opacity: 0.8;
  margin-bottom: 0.375rem;
}

.don-label-sub {
  font-size: 0.7rem;
  opacity: 0.6;
  font-style: italic;
  margin-top: 0.375rem;
}
</style>