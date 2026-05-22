---
layout: default
---

# Tools that do the legwork

<div class="text-base opacity-70 mt-2">
  Layered — each tool catches things the others miss.
</div>

<div class="grid grid-cols-3 gap-4 mt-8">

<div class="rounded-lg border border-gray-700 p-4">
  <div class="flex items-center gap-2 mb-2">
    <logos-eslint class="text-2xl" />
    <span class="font-semibold">ESLint plugins</span>
  </div>
  <div class="text-sm opacity-80 leading-relaxed">
    Catches issues <em>as you type</em>. Missing alt text, bad ARIA, unlabeled controls.
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
    Free browser extension. Scans rendered pages. Catches ~57%* of WCAG issues on average.
  </div>
  <div class="text-xs opacity-50 mt-2">
    * According to Deque's 2021 study of ~300k issues across 13,000 pages
  </div>
  <div class="text-xs opacity-50 mt-2">
    <a href="https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd" target="_blank">
      Install for Chrome
    </a>
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-4">
  <div class="flex items-center gap-2 mb-2">
    <logos-chrome class="text-2xl" />
    <span class="font-semibold">Lighthouse</span>
  </div>
  <div class="text-sm opacity-80 leading-relaxed">
    Built into Chrome DevTools. A11y + SEO + perf in one pass. Uses axe-core under the hood.
  </div>
  <div class="text-xs opacity-50 mt-2">
    DevTools → Lighthouse tab
  </div>
</div>

</div>

<div v-click class="mt-8 text-sm opacity-60 text-center">
  Honorable mention: <a href="https://storybook.js.org/addons/@storybook/addon-a11y" target="_blank"><strong>Storybook a11y addon</strong></a> — same axe engine, runs per component.
</div>


---
layout: default
transition: slide-up
---

# Labels that say nothing

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> What the tool checks
  </div>

  <div class="text-sm opacity-70 mb-3">Rule: every interactive element must have an accessible name.</div>

```html
<button aria-label="button">
  <lucide-search />
</button>

<img src="chart.png" alt="image" />
```

  <div class="text-xs opacity-60 mt-3">
    Names exist → passes the audit.
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> What actually happens
  </div>

<div class="rounded-lg border border-gray-700 p-4 mt-2 bg-gray-900 font-mono text-sm">
  <div class="opacity-60">Screen reader output:</div>
  <div class="mt-2"><lucide-volume-2 class="inline text-pink-400" /> "button, button"</div>
  <div class="mt-1"><lucide-volume-2 class="inline text-pink-400" /> "image, image"</div>
</div>

  <div class="text-xs opacity-60 mt-3">
    User has no idea <em>what</em> the button does or <em>what</em> the image shows.
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  A label only helps if it <strong>describes the thing</strong>.
</div>

---
layout: default
transition: slide-up
---

# Placeholder is not a label

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> What the tool checks
  </div>

  <div class="text-sm opacity-70 mb-3">Rule: input has an accessible name from <em>some</em> source.</div>

```html
<input
  type="text"
  placeholder="IBAN: ex. BE71 0961 2345 6769"
/>
```

  <div class="text-xs opacity-60 mt-3">
    Placeholder counts as a name → passes (with some configs).
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> What actually happens
  </div>

  <PlaceholderDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    The "label" disappears the moment the user starts typing.
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  Labels stay. Placeholders are <strong>hints</strong>, not labels.
</div>

---
layout: default
transition: slide-up
---

# Color-only meaning

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> What the tool checks
  </div>

  <div class="text-sm opacity-70 mb-3">Rule: required state is exposed via ARIA / native attributes.</div>

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
    State is in the markup → passes the audit.
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> What actually happens
  </div>

  <ColorOnlyDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    With CVD or grayscale, all fields look identical — no way to tell which is required.
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  Color is a <em>second</em> signal. There must be a <strong>first one</strong> too.
</div>

---
layout: default
---

# Where did focus go?

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> What the tool checks
  </div>

  <div class="text-sm opacity-70 mb-3">Rule: <code>:focus</code> styles are defined.</div>

```css
.btn:focus {
  outline: none;
}

/* or "reset" CSS */
button {
  outline: 0;
}
```

  <div class="text-xs opacity-60 mt-3">
    CSS rule exists → passes the audit.
  </div>
</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> What actually happens
  </div>

  <FocusDemo class="mt-2" />

  <div class="text-xs opacity-60 mt-3">
    Tab through — keyboard users have <em>no idea</em> where they are.
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-base opacity-80">
  Focus is the keyboard user's <strong>cursor</strong>.
</div>

---
layout: default
---

# A starter checklist

<div class="text-base opacity-70 text-sm">
  You don't need to know every rule from day one. Be aware of these things — and lean on the tools when in doubt.
</div>

<Checklist />
