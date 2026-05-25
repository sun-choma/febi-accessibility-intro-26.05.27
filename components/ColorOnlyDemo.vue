<script setup lang="ts">
import { ref } from 'vue'

const grayscale = ref(false)
</script>

<template>
  <div class="color-only-demo">
    <div
        class="form-group"
        :class="{ 'is-grayscale': grayscale }"
    >
      <input type="text" placeholder="名前" class="demo-input" />
      <input type="text" placeholder="会社" class="demo-input required" />
      <input type="text" placeholder="メールアドレス" class="demo-input required" />
      <input type="text" placeholder="メモ" class="demo-input" />
    </div>

    <label class="toggle">
      <input type="checkbox" v-model="grayscale" class="toggle-input" />
      <span class="toggle-track">
        <span class="toggle-thumb" />
      </span>
      <span>グレースケール</span>
    </label>
  </div>
</template>

<style scoped>
.color-only-demo {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  transition: filter 300ms ease;
  width: 100%;
}

.form-group.is-grayscale {
  filter: grayscale(1);
}

.demo-input {
  background: #1e1f29;
  border: 1px solid #44475a;
  border-radius: 0.375rem;
  padding: 0.5rem 0.75rem;
  color: #f8f8f2;
  font-size: 0.875rem;
}

.demo-input.required {
  border-color: #ff5555;
}

.demo-input:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

/* Dracula toggle (consistent with other demos) */
.toggle {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  user-select: none;
  color: #f8f8f2;
  font-size: 0.8125rem;
}
.toggle-input {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}
.toggle-track {
  position: relative;
  width: 2.5rem;
  height: 1.25rem;
  background: #44475a;
  border-radius: 999px;
}
.toggle-thumb {
  position: absolute;
  top: 0.125rem;
  left: 0.125rem;
  width: 1rem;
  height: 1rem;
  background: #f8f8f2;
  border-radius: 50%;
  transition: transform 200ms ease;
}
.toggle-input:checked + .toggle-track {
  background: #bd93f9;
}
.toggle-input:checked + .toggle-track .toggle-thumb {
  transform: translateX(1.25rem);
}
</style>