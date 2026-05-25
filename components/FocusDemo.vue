<template>
  <div class="focus-demo">
    <div class="row">
      <div class="row-label">NG</div>
      <div class="buttons bad">
        <button class="demo-btn">1</button>
        <button class="demo-btn">2</button>
        <button class="demo-btn">3</button>
      </div>
    </div>

    <div class="row">
      <div class="row-label">OK</div>
      <div class="buttons good">
        <button class="demo-btn">1</button>
        <button class="demo-btn">2</button>
        <button class="demo-btn">3</button>
      </div>
    </div>

    <div class="hint">
      <lucide-arrow-up class="inline" /> 各行に Tab で移動 — 違いを実感
    </div>
  </div>
</template>

<style scoped>
.focus-demo {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.row-label {
  width: 3rem;
  font-family: ui-monospace, monospace;
  font-size: 0.7rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  opacity: 0.5;
}

.buttons {
  display: flex;
  gap: 0.5rem;
}

.demo-btn {
  background: #44475a;
  color: #f8f8f2;
  border: 1px solid #6272a4;
  border-radius: 0.375rem;
  padding: 0.4rem 1rem;
  font-size: 0.875rem;
  cursor: pointer;
}

/* Bad: focus removed entirely */
.buttons.bad .demo-btn:focus,
.buttons.bad .demo-btn:focus-visible {
  outline: none;
}

/* Good: visible focus ring */
.buttons.good .demo-btn:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.hint {
  font-size: 0.75rem;
  opacity: 0.6;
  font-style: italic;
  margin-top: 0.5rem;
}
</style>