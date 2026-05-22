<script setup lang="ts">
import { ref } from 'vue'

const fakeChecked = ref(false)
const realChecked = ref(false)
const goodChecked = ref(false)

function toggleFake() {
  fakeChecked.value = !fakeChecked.value
}
</script>

<template>
  <div class="fake-cb-demo">
    <!-- Bad: click works, keyboard doesn't -->
    <div
        role="checkbox"
        :aria-checked="fakeChecked"
        class="fake-cb"
        @click="toggleFake"
    >
      <span class="fake-cb-box">
        <lucide-check v-if="fakeChecked" class="check" />
      </span>
      Bad
    </div>

    <!-- Native -->
    <label class="real-cb">
      <input type="checkbox" v-model="realChecked" />
      Native
    </label>

    <!-- Good: hidden native input + styled box -->
    <label class="good-cb">
      <input type="checkbox" v-model="goodChecked" class="sr-only" />
      <span class="good-cb-box" aria-hidden="true">
        <lucide-check v-if="goodChecked" class="check" />
      </span>
      Good
    </label>
  </div>
</template>

<style scoped>
.fake-cb-demo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-size: 0.875rem;
}

/* Bad */
.fake-cb {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0;
  cursor: pointer;
  user-select: none;
  /* no tabindex, no keyboard handlers — broken on purpose */
}

.fake-cb-box {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1rem;
  height: 1rem;
  border: 1px solid #6272a4;
  border-radius: 0.2rem;
  background: #1e1f29;
}

.check {
  width: 0.75rem;
  height: 0.75rem;
  color: #50fa7b;
}

/* Native */
.real-cb {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0;
  cursor: pointer;
  user-select: none;
}

.real-cb input {
  width: 1rem;
  height: 1rem;
  accent-color: #bd93f9;
  cursor: pointer;
}

/* Good: hidden native input + styled box */
.good-cb {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0;
  cursor: pointer;
  user-select: none;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

.good-cb-box {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1rem;
  height: 1rem;
  border: 1px solid #6272a4;
  border-radius: 0.2rem;
  background: #1e1f29;
  transition: background 150ms ease, border-color 150ms ease;
}

.good-cb:has(input:checked) .good-cb-box {
  background: #bd93f9;
  border-color: #bd93f9;
}

.good-cb:has(input:checked) .check {
  color: #282a36;
}

.good-cb:has(input:focus-visible) .good-cb-box {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}
</style>