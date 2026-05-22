<script setup lang="ts">
import { ref } from 'vue'

const grayscale = ref(false)

const orders = [
  { id: '#1042', customer: 'Tanaka K.', status: 'Paid', color: '#22c55e' },
  { id: '#1043', customer: 'Nguyễn T.', status: 'Pending', color: '#f59e0b' },
  { id: '#1044', customer: 'Watanabe Y.', status: 'Failed', color: '#ef4444' },
  { id: '#1045', customer: 'Trần H.', status: 'Refunded', color: '#3b82f6' },
]
</script>

<template>
  <div class="grayscale-demo">
    <div
        class="order-list transition-all duration-700"
        :class="{ 'is-grayscale': grayscale }"
    >
      <div v-for="order in orders" :key="order.id" class="order-row">
        <span class="order-id">{{ order.id }}</span>
        <span class="order-customer">{{ order.customer }}</span>
        <span class="status-badge" :style="{ background: order.color }">
          {{ order.status }}
        </span>
      </div>
    </div>

    <label class="toggle">
      <input type="checkbox" v-model="grayscale" class="toggle-input" />
      <span class="toggle-track">
        <span class="toggle-thumb" />
      </span>
      <span class="toggle-label">Grayscale</span>
    </label>
  </div>
</template>

<style scoped>
/* Dracula palette references:
   bg:        #282a36
   current:   #44475a
   fg:        #f8f8f2
   comment:   #6272a4
   purple:    #bd93f9
   pink:      #ff79c6
*/

.grayscale-demo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.order-list {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  background: #282a36;
  border: 1px solid #44475a;
  border-radius: 0.75rem;
  padding: 1rem;
  min-width: 28rem;
}

.order-list.is-grayscale {
  filter: grayscale(1);
}

.order-row {
  display: grid;
  grid-template-columns: 5rem 1fr auto;
  align-items: center;
  gap: 1rem;
  padding: 0.75rem 1rem;
  background: #44475a;
  border-radius: 0.5rem;
}

.order-id {
  font-family: ui-monospace, monospace;
  color: #6272a4;
}

.order-customer {
  color: #f8f8f2;
}

.status-badge {
  padding: 0.25rem 0.75rem;
  border-radius: 999px;
  color: white;
  font-size: 0.875rem;
  font-weight: 600;
  min-width: 5.5rem;
  text-align: center;
}

/* Dracula-styled toggle switch */
.toggle {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  cursor: pointer;
  user-select: none;
  font-size: 1rem;
  color: #f8f8f2;
}

.toggle-input {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}

.toggle-track {
  position: relative;
  width: 3rem;
  height: 1.5rem;
  background: #44475a;
  border-radius: 999px;
  transition: background 200ms ease;
}

.toggle-thumb {
  position: absolute;
  top: 0.125rem;
  left: 0.125rem;
  width: 1.25rem;
  height: 1.25rem;
  background: #f8f8f2;
  border-radius: 50%;
  transition: transform 200ms ease, background 200ms ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
}

.toggle-input:checked + .toggle-track {
  background: #bd93f9;
}

.toggle-input:checked + .toggle-track .toggle-thumb {
  transform: translateX(1.5rem);
}

.toggle-input:focus-visible + .toggle-track {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.toggle-label {
  font-weight: 500;
}
</style>