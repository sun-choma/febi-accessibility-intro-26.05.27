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

const cvd = ref<CVD>('normal')

const cvdOptions = [
  { value: 'normal' as const, label: '正常' },
  { value: 'deuteranomaly' as const, label: '2型3色覚' },
  { value: 'deuteranopia' as const, label: '2型2色覚' },
  { value: 'protanomaly' as const, label: '1型3色覚' },
  { value: 'protanopia' as const, label: '1型2色覚' },
  { value: 'tritanopia' as const, label: '3型2色覚' },
  { value: 'achromatopsia' as const, label: '全色盲' },
]

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

const filter = computed(() => cvdFilters[cvd.value] || 'none')
</script>

<template>
  <div class="color-alone-demo">
    <div class="panels" :style="{ filter }">
      <div class="panel">
        <div class="panel-label bad">色だけ</div>
        <div class="badges">
          <span class="badge-solid" style="background: #22c55e">支払済</span>
          <span class="badge-solid" style="background: #f59e0b">保留中</span>
          <span class="badge-solid" style="background: #ef4444">失敗</span>
          <span class="badge-solid" style="background: #3b82f6">返金済</span>
        </div>
      </div>

      <div class="panel">
        <div class="panel-label good">色 + アイコン + 形</div>
        <div class="badges">
          <span class="badge-soft" style="--c: #22c55e">
            <lucide-check-circle-2 /> 支払済
          </span>
          <span class="badge-outline" style="--c: #f59e0b">
            <lucide-clock /> 保留中
          </span>
          <span class="badge-solid-icon" style="background: #ef4444">
            <lucide-x-circle /> 失敗
          </span>
          <span class="badge-ghost" style="--c: #3b82f6">
            <lucide-undo-2 /> 返金済
          </span>
        </div>
      </div>
    </div>

    <SegmentedSwitch
        v-model="cvd"
        :options="cvdOptions"
        aria-label="色覚特性"
    />
  </div>
</template>

<style scoped>
.color-alone-demo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  min-width: 44rem;
  transition: filter 200ms ease;
}

.panel {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.75rem;
  padding: 1.25rem;
}

.panel-label {
  font-family: ui-monospace, monospace;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.panel-label.bad { color: #ff5555; }
.panel-label.good { color: #50fa7b; }

.badges {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: flex-start;
}

.badge-solid,
.badge-solid-icon,
.badge-soft,
.badge-outline,
.badge-ghost {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.375rem 0.875rem;
  border-radius: 0.5rem;
  font-size: 0.9375rem;
  font-weight: 600;
  width: fit-content;
}

.badge-solid {
  color: white;
}

.badge-solid-icon {
  color: white;
}

.badge-soft {
  color: var(--c);
  background: color-mix(in srgb, var(--c) 15%, transparent);
  border: 1px solid color-mix(in srgb, var(--c) 30%, transparent);
}

.badge-outline {
  color: var(--c);
  background: transparent;
  border: 1.5px solid var(--c);
}

.badge-ghost {
  color: var(--c);
  background: transparent;
}
</style>