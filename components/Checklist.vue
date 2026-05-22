<script setup lang="ts">
import { ref } from 'vue'

const items = ref([
  {
    title: 'Tab through the page',
    detail: 'Can you reach everything? Is focus visible? Does the order make sense?',
    checked: false,
  },
  {
    title: 'Zoom to 200%',
    detail: 'Does the layout still work? Anything cut off or overlapping?',
    checked: false,
  },
  {
    title: 'Toggle grayscale / vision emulation',
    detail: 'DevTools → Rendering → Emulate vision deficiencies. Anything carried only by color?',
    checked: false,
  },
  {
    title: 'Run Lighthouse / axe',
    detail: 'DevTools → Lighthouse → Accessibility. Fix what it flags before merging.',
    checked: false,
  },
  {
    title: 'Try a screen reader on the critical flow',
    detail: 'VoiceOver: Cmd+F5. Does it announce what matters? Focus on form / checkout / search.',
    checked: false,
  },
])
</script>

<template>
  <ul class="checklist">
    <li v-for="(item, i) in items" :key="i">
      <label class="check-item">
        <input
            type="checkbox"
            v-model="item.checked"
            class="sr-only"
        />
        <span class="check-box" aria-hidden="true">
          <lucide-check v-if="item.checked" class="check-mark" />
        </span>
        <span class="check-content" :class="{ 'is-done': item.checked }">
          <span class="check-title">{{ item.title }}</span>
          <span class="check-detail">{{ item.detail }}</span>
        </span>
      </label>
    </li>
  </ul>
</template>

<style scoped>
.checklist {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-top: 1rem;
}

.check-item {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  padding: 0.75rem 1rem;
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.5rem;
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

.check-box {
  flex-shrink: 0;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1.25rem;
  height: 1.25rem;
  border: 1.5px solid #6272a4;
  border-radius: 0.25rem;
  background: transparent;
  margin-top: 0.125rem;
  transition: background 200ms ease, border-color 200ms ease;
}

.check-item:has(input:checked) .check-box {
  background: #bd93f9;
  border-color: #bd93f9;
}

.check-item:has(input:focus-visible) .check-box {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.check-mark {
  width: 0.875rem;
  height: 0.875rem;
  color: #282a36;
}

.check-content {
  display: flex;
  flex-direction: column;
  transition: opacity 200ms ease;
  line-height: 1.5;
}

.check-content.is-done {
  text-decoration: line-through;
  opacity: 0.45;
}

.check-title {
  font-weight: 600;
}

.check-detail {
  font-size: 0.875rem;
  opacity: 0.75;
}

.check-content.is-done .check-detail {
  opacity: 1;
}
</style>