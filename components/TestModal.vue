<template>
  <div v-if="isOpen" style="position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.5); display: flex; align-items: center; justify-content: center; z-index: 1000;" @click="closeModal">
    <div style="background: white; padding: 20px; border-radius: 8px; max-width: 400px;" @click.stop>
      <h3>Test Modal</h3>
      <p>This is a simple test modal</p>
      <button @click="closeModal" style="margin-right: 10px; padding: 8px 16px; background: #ccc; border: none; border-radius: 4px; cursor: pointer;">Close</button>
      <button @click="handleCtaClick" style="padding: 8px 16px; background: #1A76BC; color: white; border: none; border-radius: 4px; cursor: pointer;">CTA</button>
    </div>
  </div>
</template>

<script setup>
// Props
defineProps({
  isOpen: {
    type: Boolean,
    default: false
  }
})

// Emits
const emit = defineEmits(['close', 'cta-click'])

// Methods
const closeModal = () => {
  emit('close')
}

const handleCtaClick = () => {
  emit('cta-click')
}
</script>
