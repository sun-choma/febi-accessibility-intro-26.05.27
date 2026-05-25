<script setup lang="ts">
import { ref, computed } from 'vue'
import SegmentedSwitch from './SegmentedSwitch.vue'

type CVD =
    | 'normal'
    | 'deuteranomaly'
    | 'deuteranopia'
    | 'protanomaly'
    | 'protanopia'
    | 'tritanopia'
    | 'achromatopsia'

type BlurLevel = 0 | 1 | 2 | 4

const cvd = ref<CVD>('normal')
const blurLevel = ref<BlurLevel>(0)

const cvdOptions = [
  { value: 'normal' as const, label: '正常' },
  { value: 'deuteranomaly' as const, label: '2型3色覚' },
  { value: 'deuteranopia' as const, label: '2型2色覚' },
  { value: 'protanomaly' as const, label: '1型3色覚' },
  { value: 'protanopia' as const, label: '1型2色覚' },
  { value: 'tritanopia' as const, label: '3型2色覚' },
  { value: 'achromatopsia' as const, label: '全色盲' },
]

const blurOptions = [
  { value: 0 as const, label: 'なし' },
  { value: 1 as const, label: '弱' },
  { value: 2 as const, label: '中' },
  { value: 4 as const, label: '強' },
]

// CVD matrices from @storybook/addon-a11y (ColorFilters.tsx).
// Blur stdDeviation values reference Chrome DevTools' kBlurredVision (stdDeviation=2).
const cvdFilters: Record<CVD, string> = {
  normal: '',
  deuteranomaly:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.8 0.2 0 0 0 0.258 0.742 0 0 0 0 0.142 0.858 0 0 0 0 0 1 0'/></filter></svg>#f\")",
  deuteranopia:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.625 0.375 0 0 0 0.7 0.3 0 0 0 0 0.3 0.7 0 0 0 0 0 1 0'/></filter></svg>#f\")",
  protanomaly:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.817 0.183 0 0 0 0.333 0.667 0 0 0 0 0.125 0.875 0 0 0 0 0 1 0'/></filter></svg>#f\")",
  protanopia:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.567 0.433 0 0 0 0.558 0.442 0 0 0 0 0.242 0.758 0 0 0 0 0 1 0'/></filter></svg>#f\")",
  tritanopia:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.95 0.05 0 0 0 0 0.433 0.567 0 0 0 0.475 0.525 0 0 0 0 0 1 0'/></filter></svg>#f\")",
  achromatopsia:
      "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'><filter id='f'><feColorMatrix values='0.299 0.587 0.114 0 0 0.299 0.587 0.114 0 0 0.299 0.587 0.114 0 0 0 0 0 1 0'/></filter></svg>#f\")",
}

const filter = computed(() => {
  const parts: string[] = []
  if (blurLevel.value > 0) parts.push(`blur(${blurLevel.value}px)`)
  if (cvdFilters[cvd.value]) parts.push(cvdFilters[cvd.value])
  return parts.length ? parts.join(' ') : 'none'
})
</script>

<template>
  <div class="vision-demo">
    <div class="samples-wrap">
      <div class="samples" :style="{ filter }">
        <div class="texts">
          <div class="sample">
            <div class="label">合格 — 4.5:1</div>
            <p class="body-text pass">
              注文を確定する前に、配送先の住所をご確認ください。
              アカウント設定からあとで変更することもできます。
            </p>
          </div>

          <div class="sample">
            <div class="label">不合格 — 2.15:1</div>
            <p class="body-text fail">
              注文を確定する前に、配送先の住所をご確認ください。
              アカウント設定からあとで変更することもできます。
            </p>
          </div>
        </div>

        <hr class="divider" />

        <div class="badges">
          <span class="badge" style="background: #22c55e">支払済</span>
          <span class="badge" style="background: #f59e0b">保留中</span>
          <span class="badge" style="background: #ef4444">失敗</span>
          <span class="badge" style="background: #3b82f6">返金済</span>
        </div>
      </div>
    </div>

    <div class="controls">
      <SegmentedSwitch
          v-model="cvd"
          :options="cvdOptions"
          aria-label="色覚特性"
      />

      <SegmentedSwitch
          v-model="blurLevel"
          :options="blurOptions"
          aria-label="ぼかしレベル"
      />
    </div>
  </div>
</template>

<style scoped>
.vision-demo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.samples-wrap {
  overflow: hidden;
  border-radius: 0.75rem;
}

.samples {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.75rem;
  padding: 1.5rem;
  min-width: 44rem;
  transition: filter 200ms ease;
}

.texts {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.sample {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.label {
  font-family: ui-monospace, monospace;
  font-size: 0.75rem;
  color: #6272a4;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.body-text {
  font-size: 0.9375rem;
  line-height: 1.5;
  margin: 0;
}

.body-text.pass { color: #f8f8f2; }
.body-text.fail { color: #5c5c65; }

.divider {
  border: none;
  border-top: 1px solid #44475a;
  margin: 0;
}

.badges {
  display: flex;
  gap: 0.75rem;
  justify-content: center;
}

.badge {
  padding: 0.25rem 0.75rem;
  border-radius: 999px;
  color: white;
  font-size: 0.8125rem;
  font-weight: 600;
}

.controls {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
}
</style>