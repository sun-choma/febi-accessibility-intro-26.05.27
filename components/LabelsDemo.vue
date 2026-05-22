<template>
  <div class="labels-demo">
    <!-- Inputs -->
    <div class="row-label">Inputs</div>

    <div class="demo-panel bad">
      <div class="panel-label">Bad</div>
      <input type="email" class="demo-input" />
    </div>

    <div class="demo-panel good">
      <div class="panel-label">Good</div>
      <label for="lbl-email" class="demo-label">Email</label>
      <input id="lbl-email" type="email" class="demo-input" />
    </div>

    <!-- Icon buttons -->
    <div class="row-label">Icon buttons</div>

    <div class="demo-panel bad">
      <div class="panel-label">Bad</div>
      <button class="demo-icon-btn">
        <lucide-x />
      </button>
    </div>

    <div class="demo-panel good">
      <div class="panel-label">Good</div>
      <button class="demo-icon-btn" aria-label="Close dialog">
        <lucide-x />
      </button>
    </div>

    <!-- Form errors -->
    <div class="row-label">Form errors</div>

    <div class="demo-panel bad">
      <div class="panel-label">Bad</div>
      <label for="lbl-err-bad" class="demo-label">Email</label>
      <input
          id="lbl-err-bad"
          type="email"
          class="demo-input"
          aria-invalid="true"
          value="not-an-email"
      />
      <p class="demo-error">Must be a valid email.</p>
    </div>

    <div class="demo-panel good">
      <div class="panel-label">Good</div>
      <label for="lbl-err-good" class="demo-label">Email</label>
      <input
          id="lbl-err-good"
          type="email"
          class="demo-input"
          aria-invalid="true"
          aria-describedby="lbl-err-good-msg"
          value="not-an-email"
      />
      <p id="lbl-err-good-msg" class="demo-error">Must be a valid email.</p>
    </div>
  </div>
</template>

<style scoped>
.labels-demo {
  display: grid;
  grid-template-columns: 10rem 1fr 1fr;
  gap: 1rem 1rem;
  align-items: start;
}

.row-label {
  align-self: center;
  font-family: ui-monospace, monospace;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  opacity: 0.5;
}

.demo-panel {
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.5rem;
  padding: 0.875rem 1rem;
}
.demo-panel.bad { border-left: 3px solid #ff5555; }
.demo-panel.good { border-left: 3px solid #50fa7b; }

.panel-label {
  font-family: ui-monospace, monospace;
  font-size: 0.6875rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  opacity: 0.5;
  margin-bottom: 0.5rem;
}

.demo-label {
  display: block;
  font-size: 0.8125rem;
  margin-bottom: 0.25rem;
  opacity: 0.85;
}

.demo-input {
  width: 100%;
  background: #1e1f29;
  border: 1px solid #44475a;
  border-radius: 0.375rem;
  padding: 0.4rem 0.625rem;
  color: #f8f8f2;
  font-size: 0.875rem;
}
.demo-input:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.demo-icon-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2rem;
  height: 2rem;
  background: transparent;
  border: 1px solid #44475a;
  border-radius: 0.375rem;
  color: #f8f8f2;
  cursor: pointer;
}
.demo-icon-btn:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.demo-error {
  margin: 0.5rem 0 0;
  font-size: 0.8125rem;
  color: #ff5555;
}
</style>