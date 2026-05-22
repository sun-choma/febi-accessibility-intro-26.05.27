---
layout: default
---

# What is accessibility?

Making digital products usable by <strong>everyone</strong> —
regardless of ability, device, or context.

<div class="mt-12 text-2xl italic opacity-80">

> "The power of the Web is in its <span v-mark.underline.cyan>universality</span>.
> Access by everyone regardless of disability is an essential aspect."

</div>

<div class="mt-4 text-right text-sm opacity-60">

— Tim Berners-Lee, inventor of the World Wide Web

</div>

<v-clicks at="2">

- Not a feature you add at the end
- Not a checklist you tick off
- A <span v-mark.circle.pink>quality</span> of the product, like performance or security

</v-clicks>


---
layout: default
---

# The grayscale test

Same UI. Different users see different things.

<GrayscaleDemo class="mt-12" />

---
layout: default
---

# WCAG — the rulebook

**Web Content Accessibility Guidelines** — the international standard for digital accessibility, maintained by the W3C.

<div class="mt-8 text-sm opacity-70">
  Organized around four principles, often abbreviated <strong>POUR</strong>:
</div>

<div class="grid grid-cols-4 gap-3 mt-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">P</div>
    <div class="text-sm font-semibold mt-1">Perceivable</div>
    <div class="text-xs opacity-60 mt-1">Users can sense the content</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">O</div>
    <div class="text-sm font-semibold mt-1">Operable</div>
    <div class="text-xs opacity-60 mt-1">Users can interact with it</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">U</div>
    <div class="text-sm font-semibold mt-1">Understandable</div>
    <div class="text-xs opacity-60 mt-1">Content and UI make sense</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">R</div>
    <div class="text-sm font-semibold mt-1">Robust</div>
    <div class="text-xs opacity-60 mt-1">Works with assistive tech</div>
  </div>
</div>

<div class="mt-10 text-sm opacity-70">
  Three conformance levels, increasingly strict:
</div>

<div class="grid grid-cols-3 gap-3 mt-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-xl font-bold text-purple-400">A</div>
    <div class="text-sm opacity-80 mt-1">Bare minimum</div>
    <div class="text-xs opacity-50 mt-1">Without this, content is broken for many users</div>
  </div>
  <div class="rounded-lg border-2 border-pink-400 px-4 py-3">
    <div class="text-xl font-bold text-pink-400">AA</div>
    <div class="text-sm opacity-80 mt-1">Practical standard</div>
    <div class="text-xs opacity-50 mt-1">What most projects, laws, and tools target</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-xl font-bold text-purple-400">AAA</div>
    <div class="text-sm opacity-80 mt-1">Gold standard</div>
    <div class="text-xs opacity-50 mt-1">Rarely required end-to-end; specific contexts</div>
  </div>
</div>

<div class="mt-6 text-xs opacity-50 text-center">
  <a href="https://web.dev/learn/accessibility/measure#wcag" target="_blank">
    <carbon-link class="inline" /> web.dev — Learn Accessibility · WCAG
  </a>
</div>

---
layout: default
transition: slide-up
---

# Color & contrast

WCAG AA — the level most projects target.

<div class="grid grid-cols-2 gap-8 mt-8">

<div class="rounded-lg p-6 border border-gray-600">
  <div class="text-5xl font-bold text-pink-400">4.5:1</div>
  <div class="mt-2 opacity-80">Body text</div>
  <div class="mt-1 text-sm opacity-50">Anything below 18pt / 14pt bold</div>
</div>

<div class="rounded-lg p-6 border border-gray-600">
  <div class="text-5xl font-bold text-pink-400">3:1</div>
  <div class="mt-2 opacity-80">Large text & UI components</div>
  <div class="mt-1 text-sm opacity-50">18pt+ or 14pt+ bold, icons, borders</div>
</div>

</div>

<ContrastDemo class="mt-10" />

<div class="mt-6 text-sm opacity-60">

DevTools → Inspect element → contrast ratio shown in the color picker

</div>

---

# Why those numbers exist

<div class="text-sm opacity-60" style="view-transition-name: ratio-aa"/>

<ContrastVisionDemo />

---
layout: default
---

# Numbers behind the users

<div class="mt-6">

<div class="text-sm opacity-60 mb-3">Color vision deficiency, by type — share of men affected:</div>

<div class="grid grid-cols-4 gap-3">
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~5%</div>
    <div class="text-sm opacity-80 mt-1">Deuteranomaly</div>
    <div class="text-xs opacity-50">reduced green sensitivity</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~1.2%</div>
    <div class="text-sm opacity-80 mt-1">Deuteranopia</div>
    <div class="text-xs opacity-50">no green cones</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">~1%</div>
    <div class="text-sm opacity-80 mt-1">Protanomaly / Protanopia</div>
    <div class="text-xs opacity-50">reduced red / no red cones</div>
  </div>
  <div class="rounded-lg border border-gray-700 px-4 py-3">
    <div class="text-2xl font-bold text-pink-400">&lt;0.01%</div>
    <div class="text-sm opacity-80 mt-1">Tritan- / Achromatopsia</div>
    <div class="text-xs opacity-50">blue-yellow / total</div>
  </div>
</div>

</div>

<div v-click class="mt-10 text-center text-lg opacity-70">
  Sum it up, across the global population —
</div>

<div class="grid grid-cols-3 gap-8 mt-6">

<div v-click class="text-center">
  <div class="text-6xl font-bold text-pink-400">1 in 12</div>
  <div class="mt-2 text-base opacity-80">men have</div>
  <div class="text-base opacity-80">color vision deficiency</div>
</div>

<div v-click class="text-center">
  <div class="text-6xl font-bold text-pink-400">1.3B</div>
  <div class="mt-2 text-base opacity-80">people live with</div>
  <div class="text-base opacity-80">significant disability</div>
</div>

<div v-click class="text-center" v-mark.circle.pink>
  <div class="text-6xl font-bold text-pink-400">16%</div>
  <div class="mt-2 text-base opacity-80">of the world —</div>
  <div class="text-base opacity-80">about 1 in 6 people</div>
</div>

</div>

<div v-click class="mt-10 text-center text-lg opacity-80">
  These aren't edge cases. They're a sizable portion of every team's audience.
</div>

<div v-click class="mt-2 text-center text-xs opacity-40">
  Sources: Colour Blind Awareness · WHO Global Report on Disability (2023)
</div>

---
layout: default
---

# Don't rely on color alone

<ColorAloneDemo class="mt-8" />

<div v-click class="mt-8 text-center text-lg opacity-80" click="1">
  Shapes and icons help to convey the message <strong>alongside</strong> colors
</div>

---
layout: default
---

# It's not just color

<div class="mt-6 text-lg opacity-80">
  Same need. Different cause.
</div>

<div class="grid grid-cols-3 gap-3 mt-6">

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">Permanent</div>
    <div class="text-3xl mb-2"><lucide-hand class="inline" /></div>
    <div class="text-sm">One arm</div>
  </div>

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">Temporary</div>
    <div class="text-3xl mb-2"><lucide-bandage class="inline" /></div>
    <div class="text-sm">Arm in a cast</div>
  </div>

  <div class="rounded-lg border border-gray-700 p-4 text-center">
    <div class="text-xs font-mono uppercase tracking-wider opacity-50 mb-2">Situational</div>
    <div class="text-3xl mb-2"><lucide-baby class="inline" /></div>
    <div class="text-sm">Holding a baby</div>
  </div>

</div>

<div v-click class="mt-8 text-center text-base opacity-70">
  All three need one-handed UI. The accessibility solution serves all three.
</div>

<div v-click class="mt-10">

<div class="text-sm opacity-60 mb-3">The full picture — four kinds of impairment, three permanence levels each:</div>

<div class="grid grid-cols-4 gap-2 text-sm">
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">Vision</div>
    <div class="text-xs opacity-60">blindness · low vision · CVD</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">Motor</div>
    <div class="text-xs opacity-60">paralysis · tremors · RSI</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">Cognitive</div>
    <div class="text-xs opacity-60">dyslexia · ADHD · memory</div>
  </div>
  <div class="rounded-md bg-gray-800 px-3 py-2">
    <div class="font-semibold opacity-90 mb-1">Hearing</div>
    <div class="text-xs opacity-60">deafness · partial loss</div>
  </div>
</div>

</div>

<div v-click class="mt-8 text-center text-lg">
  Build for the <span v-mark.circle.pink>spectrum</span>, not the average.
</div>

---
layout: default
---

# Why it matters more now

<div class="grid grid-cols-3 gap-6 mt-8">

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-users /></div>
  <div class="font-semibold text-lg mb-2">Demographic shift</div>
  <div class="text-sm opacity-80 leading-relaxed">
    Populations are aging — <strong>~29% of Japan is 65+</strong> (record high, 2025). Age brings vision loss, motor decline, cognitive load.
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    The "average user" is shifting toward needing what we call accessibility features.
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-smartphone /></div>
  <div class="font-semibold text-lg mb-2">Mobile &amp; context</div>
  <div class="text-sm opacity-80 leading-relaxed">
    Phones put everyone in temporary impairment — outdoor glare, one-handed use on a train, noisy cafés, tiny touch targets.
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    Your users are <em>already</em> hitting the accessibility wall. They just don't call it that.
  </div>
</div>

<div class="rounded-lg border border-gray-700 p-5">
  <div class="text-pink-400 text-3xl mb-3"><lucide-trending-up /></div>
  <div class="font-semibold text-lg mb-2">SEO &amp; dev payoff</div>
  <div class="text-sm opacity-80 leading-relaxed">
    Semantic HTML, alt text, heading hierarchy, ARIA — Google reads all of these as ranking signals.
  </div>
  <div class="text-sm opacity-80 mt-3 leading-relaxed">
    Same effort, two wins: <strong>better Lighthouse scores</strong> and a <strong>more accessible product</strong>.
  </div>
</div>

</div>
