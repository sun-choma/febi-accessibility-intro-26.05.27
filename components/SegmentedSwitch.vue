<script setup lang="ts" generic="T extends string | number">
import {ref, watch, nextTick, useTemplateRef} from 'vue'
import {onMounted, onUnmounted} from 'vue'


const props = defineProps<{
  options: { value: T; label: string }[]
  modelValue: T
  ariaLabel?: string
}>()

const emit = defineEmits<{
  'update:modelValue': [value: T]
}>()

const buttonRefs = ref<HTMLButtonElement[]>([])

const thumbStyle = ref<{ left: string; width: string }>({left: '0px', width: '0px'})

function updateThumb() {
  const activeIdx = props.options.findIndex(o => o.value === props.modelValue)
  const btn = buttonRefs.value[activeIdx]
  if (!btn) return
  thumbStyle.value = {
    left: `${btn.offsetLeft}px`,
    width: `${btn.offsetWidth}px`,
  }
}

watch(
    () => props.modelValue,
    () => nextTick(updateThumb),
    {immediate: true}
)


onMounted(() => {
  nextTick(updateThumb)
  window.addEventListener('resize', updateThumb)
})
onUnmounted(() => {
  window.removeEventListener('resize', updateThumb)
})

function select(value: T) {
  emit('update:modelValue', value)
}

function setButtonRef(el: any, idx: number) {
  if (el) buttonRefs.value[idx] = el as HTMLButtonElement
}
</script>

<template>
  <div
      ref="track"
      class="segmented"
      role="radiogroup"
      :aria-label="ariaLabel"
  >
    <div class="thumb" :style="thumbStyle" aria-hidden="true"/>
    <button
        v-for="(opt, idx) in options"
        :key="String(opt.value)"
        :ref="el => setButtonRef(el, idx)"
        class="segment"
        :class="{ 'is-active': opt.value === modelValue }"
        role="radio"
        :aria-checked="opt.value === modelValue"
        @click="select(opt.value)"
    >
      {{ opt.label }}
    </button>
  </div>
</template>

<style scoped>
.segmented {
  position: relative;
  display: inline-flex;
  background: #44475a;
  border-radius: 999px;
  padding: 0.25rem;
  gap: 0.125rem;
}

.thumb {
  position: absolute;
  top: 0.25rem;
  bottom: 0.25rem;
  background: #bd93f9;
  border-radius: 999px;
  transition: left 300ms cubic-bezier(0.4, 0, 0.2, 1),
  width 300ms cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 2px 6px rgba(189, 147, 249, 0.3);
  z-index: 0;
}

.segment {
  position: relative;
  z-index: 1;
  padding: 0.5rem 1.25rem;
  font-size: 0.9375rem;
  font-weight: 500;
  color: #f8f8f2;
  background: transparent;
  border: none;
  border-radius: 999px;
  cursor: pointer;
  transition: color 200ms ease;
}

.segment.is-active {
  color: #282a36;
  font-weight: 600;
}

.segment:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.segment:not(.is-active):hover {
  color: #ff79c6;
}
</style>