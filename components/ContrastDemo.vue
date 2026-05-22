<script setup lang="ts">
const examples = [
  {label: 'Comment gray', fg: '#4e5b81', ratio: 2.12, pass: false},
  {label: 'Foreground', fg: '#f8f8f2', ratio: 13.35, pass: true},
  {label: 'Purple', fg: '#bd93f9', ratio: 5.9, pass: true},
]
</script>

<template>
  <div class="contrast-demo">
    <div
        v-for="ex in examples"
        :key="ex.label"
        class="sample"
        :style="{ color: ex.fg }"
    >
      <span class="text">The quick brown fox</span>
      <span class="ratio" :class="{ fail: !ex.pass }">
        {{ ex.ratio.toFixed(2) }}:1
        <span class="badge">{{ ex.pass ? '✓ AA' : '✗ AA' }}</span>
      </span>
    </div>
  </div>
</template>

<style scoped>
.contrast-demo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.5rem;
  padding: 1rem 1.5rem;
}

.sample {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  font-size: 1.125rem;
}

.text {
  font-family: ui-sans-serif, system-ui, sans-serif;
}

.ratio {
  font-family: ui-monospace, monospace;
  font-size: 0.875rem;
  color: #f8f8f2;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.ratio.fail {
  color: #ff5555;
}

.badge {
  font-size: 0.75rem;
  padding: 0.125rem 0.5rem;
  border-radius: 999px;
  background: rgba(80, 250, 123, 0.15);
  color: #50fa7b;
  border: 1px solid rgba(80, 250, 123, 0.3);
}

.ratio.fail .badge {
  background: rgba(255, 85, 85, 0.15);
  color: #ff5555;
  border-color: rgba(255, 85, 85, 0.3);
}
</style>