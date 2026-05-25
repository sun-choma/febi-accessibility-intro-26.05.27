<script setup lang="ts">
import { ref } from 'vue'

const value = ref('')
</script>

<template>
  <div class="placeholder-demo">
    <input
        type="text"
        placeholder="IBAN: 例 BE71 0961 2345 6769"
        v-model="value"
        class="demo-input"
    />
    <div class="hint">
      <lucide-arrow-up class="inline" /> 入力してみよう — 4文字区切りだっけ?スペース入れる?国コードはどこ?
    </div>
  </div>
</template>

<style scoped>
.placeholder-demo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: stretch;
  padding: 0.5rem 0;
}

.demo-input {
  background: #1e1f29;
  border: 1px solid #44475a;
  border-radius: 0.375rem;
  padding: 0.6rem 0.75rem;
  color: #f8f8f2;
  font-size: 1rem;
}

.demo-input:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.hint {
  font-size: 0.75rem;
  opacity: 0.6;
  font-style: italic;
}
</style>