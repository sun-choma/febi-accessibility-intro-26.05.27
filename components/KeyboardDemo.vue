<script setup lang="ts">
import {ref, useTemplateRef} from 'vue'

const dialog = useTemplateRef<HTMLDialogElement>('dialog')

function open() {
  dialog.value?.showModal()
}
</script>

<template>
  <div class="keyboard-demo">
    <button class="trigger" @click="open">
      Open dialog
    </button>

    <dialog ref="dialog" class="modal">
      <form method="dialog">
        <h2>Delivery option</h2>

        <fieldset>
          <legend>Speed</legend>
          <label><input type="radio" name="speed" value="standard" checked/> Standard</label>
          <label><input type="radio" name="speed" value="express"/> Express</label>
          <label><input type="radio" name="speed" value="overnight"/> Overnight</label>
        </fieldset>

        <div class="actions">
          <button value="cancel">Cancel</button>
          <button value="confirm" class="primary">Confirm</button>
        </div>
      </form>
    </dialog>
  </div>
</template>

<style scoped>
.keyboard-demo {
  display: flex;
  justify-content: center;
  padding: 2rem 0;
}

.trigger {
  padding: 0.5rem 1.25rem;
  border-radius: 0.5rem;
  background: #bd93f9;
  color: #282a36;
  border: none;
  font-size: 0.9375rem;
  font-weight: 600;
  cursor: pointer;
}

.trigger:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.modal {
  background: #282a36;
  color: #f8f8f2;
  border: 1px solid #44475a;
  border-radius: 0.75rem;
  padding: 1.5rem;
  min-width: 22rem;
}

.modal::backdrop {
  background: rgba(0, 0, 0, 0.6);
}

.modal h2 {
  margin: 0 0 1rem;
  font-size: 1.125rem;
  font-weight: 600;
}

.modal fieldset {
  border: 1px solid #44475a;
  border-radius: 0.5rem;
  padding: 0.75rem 1rem;
  margin: 0;
}

.modal legend {
  padding: 0 0.5rem;
  font-size: 0.8125rem;
  color: #6272a4;
}

.modal label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0;
  font-size: 0.9375rem;
  cursor: pointer;
}

.modal input[type='radio']:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.actions {
  display: flex;
  gap: 0.5rem;
  justify-content: flex-end;
  margin-top: 1.25rem;
}

.actions button {
  padding: 0.4rem 1rem;
  border-radius: 0.375rem;
  background: transparent;
  border: 1px solid #44475a;
  color: #f8f8f2;
  font-size: 0.875rem;
  cursor: pointer;
}

.actions button:focus-visible {
  outline: 2px solid #ff79c6;
  outline-offset: 2px;
}

.actions button.primary {
  background: #bd93f9;
  color: #282a36;
  border-color: #bd93f9;
  font-weight: 600;
}
</style>