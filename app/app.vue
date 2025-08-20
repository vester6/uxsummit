<template>
  <div>
    <NuxtRouteAnnouncer />
    
    <!-- Test the Modal Component -->
    <div style="padding: 20px;">
      <h1>Nuxt App with Figma Modal</h1>
      <p>Modal state: {{ isModalOpen ? 'Open' : 'Closed' }}</p>
      <button @click="openModal" style="padding: 10px 20px; background: #1A76BC; color: white; border: none; border-radius: 4px; cursor: pointer;">
        Open Modal
      </button>
    </div>

    <!-- Modal Component -->
    <SimpleModal 
      :is-open="isModalOpen" 
      @close="closeModal"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SimpleModal from '../components/SimpleModal.vue'

// Modal state - using explicit imports to ensure registration
const isModalOpen = ref(false)

// Modal methods
const openModal = () => {
  isModalOpen.value = true
}

const closeModal = () => {
  isModalOpen.value = false
}

</script>
