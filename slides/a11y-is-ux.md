---
layout: default
---

# Semantic HTML is 80% of the work

<div class="grid grid-cols-2 gap-6 mt-6">

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-2">
    <lucide-x class="inline" /> Custom
  </div>

```html
<div class="btn" onclick="submit()">
  Submit
</div>
```

</div>

<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-2">
    <lucide-check class="inline" /> Native
  </div>

```html
<button type="submit">
  Submit
</button>
```

</div>

</div>

<div class="mt-6">

| Feature | `<div onclick>` | `<button>` |
|---|:-:|:-:|
| Keyboard focusable | ❌ | ✅ |
| Activates on Enter / Space | ❌ | ✅ |
| Announces as "button" to screen readers | ❌ | ✅ |
| Disabled state (`:disabled`, won't fire) | ❌ | ✅ |

</div>

<div class="mt-6 text-center text-base opacity-80">
  When going custom its <span v-mark.underline.pink>your responsibility</span> to support all these features
</div>

---
layout: default
---

# Keyboard-first

<div class="text-lg opacity-80 mt-2">
  Power users live here. Devs live here. Why wouldn't your users?
</div>

<div class="grid grid-cols-2 gap-8 mt-8">

<div>
  <KeyboardDemo />
</div>

<div>

```html
<dialog>
  <form method="dialog">
    <h2>Delivery option</h2>

    <fieldset>
      <legend>Speed</legend>
      <label><input type="radio" name="speed" /> Standard</label>
      <label><input type="radio" name="speed" /> Express</label>
      <label><input type="radio" name="speed" /> Overnight</label>
    </fieldset>

    <button>Cancel</button>
    <button>Confirm</button>
  </form>
</dialog>
```

</div>

</div>

<div class="mt-6 grid grid-cols-4 gap-3 text-sm">
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Tab</kbd> — move between fields & buttons
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>↑</kbd> <kbd>↓</kbd> — select radio option
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Enter</kbd> — activate / submit
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <kbd>Esc</kbd> — close dialog
  </div>
</div>

<div v-click class="mt-6 text-center text-sm opacity-70">
  We covered <code>&lt;dialog&gt;</code> in detail in the
  <a href="LINK_TO_FEBI_CSS_DECK" target="_blank" class="underline">previous deck</a>.
  All of this is native — no JS keyboard handling.
</div>

---
layout: default
---

# Labels & names

<div class="text-lg opacity-80 mt-2">
  Every interactive element needs a name screen readers can speak.
</div>

<div class="mt-6 grid grid-cols-[10rem_1fr_1fr] gap-x-4 gap-y-6 items-start text-sm">

<div class="text-xs uppercase tracking-wider opacity-50 self-center">Inputs</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> No <code>&lt;label&gt;</code> — screen reader has nothing to say</div>

```html
<input type="email" />
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>&lt;label for&gt;</code> ties text to the input</div>

```html
<label for="email">Email</label>
<input id="email" type="email" />
```

</div>

<div class="text-xs uppercase tracking-wider opacity-50 self-center">Icon buttons</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> Icon only — announced as "button" with no purpose</div>

```html
<button>
  <lucide-x />
</button>
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>aria-label</code> provides the missing name</div>

```html
<button aria-label="Close dialog">
  <lucide-x />
</button>
```

</div>

<div class="text-xs uppercase tracking-wider opacity-50 self-center">Form errors</div>

<div>
  <div class="text-xs text-red-400 mb-2"><lucide-x class="inline" /> Error not linked — read in isolation, no context</div>

```html
<input id="email" aria-invalid="true" />
<p>Must be a valid email.</p>
```

</div>

<div>
  <div class="text-xs text-green-400 mb-2"><lucide-check class="inline" /> <code>aria-describedby</code> ties the error to the input</div>

```html
<input
  id="email"
  aria-invalid="true"
  aria-describedby="email-err"
/>
<p id="email-err">Must be a valid email.</p>
```

</div>

</div>

---
layout: default
---

# Labels in action <carbon-volume-up class="inline" />

<div class="text-sm opacity-60 mt-1">
  Cmd+F5 to toggle VoiceOver — then Tab through each side.
</div>

<LabelsDemo class="mt-6" />

---
layout: default
---

# ARIA — the careful part

<blockquote class="mt-4 pl-4 border-l-4 border-pink-400">
  <div class="text-base italic">"The first rule of ARIA: don't use ARIA."</div>
  <div class="mt-1 text-xs opacity-50">— W3C, ARIA Authoring Practices</div>
</blockquote>

<div class="grid grid-cols-2 gap-6 mt-6 text-sm">

<!-- DON'T column -->
<div>
  <div class="text-xs font-mono uppercase tracking-wider text-red-400 mb-3"><lucide-x class="inline" /> Don't</div>

  <div class="don-block">
    <div class="don-label">Redundant — <code>&lt;button&gt;</code> already has the role</div>

```html
<button role="button">Save</button>
```
  </div>

<div class="don-block">
  <div class="don-label">Rebuilding native — try tabbing and pressing Space</div>

  <CustomCheckboxDemo class="mt-2" />
</div>

<div class="don-block">
  <div class="don-label">Ghost subtree — focusable children become silent</div>

```html
<div aria-hidden="true">
  <h2>Decorative section</h2>
  <button>Read more</button>
</div>
```
</div>
</div>

<!-- DO column -->
<div>
  <div class="text-xs font-mono uppercase tracking-wider text-green-400 mb-3"><lucide-check class="inline" /> Do</div>

  <div class="do-block">
    <div class="do-label">Name icon-only buttons</div>

```html
<button aria-label="Close dialog">
  <lucide-x />
</button>
```
  </div>

  <div class="do-block">
    <div class="do-label">Announce dynamic updates</div>

```html
<div aria-live="polite" role="status">
  Saved.
</div>
```
  </div>

  <div class="do-block">
    <div class="do-label">Communicate state on toggles</div>

```html
<button aria-expanded="false" aria-controls="menu">
  Menu
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