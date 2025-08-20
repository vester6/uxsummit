<template>
  <div v-if="isOpen" class="modal-overlay" @click="closeModal">
    <div class="modal" @click.stop>
      <!-- Close Button -->
      <button class="close-button" @click="closeModal">
        <svg width="16" height="18" viewBox="0 0 16 18" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M15 1L1 17M1 1L15 17" stroke="#0C0931" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>

      <!-- Video Placeholder -->
      <div class="video-placeholder"></div>

      <!-- Content Section -->
      <div class="content-section">
        <div class="intro">
          <h2 class="title">Modal with video and button</h2>
          <p class="description">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
          </p>
        </div>

        <!-- CTA Button -->
        <button class="cta-button" @click="handleCtaClick">
          Click to see what happens...
        </button>
      </div>
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

<style scoped>
/* Import fonts */
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;600&display=swap');

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  position: relative;
  width: 595px;
  height: 646px;
  background: #FFFFFF;
  border-radius: 6px;
  box-shadow: 0px 0px 60px 0px rgba(203, 238, 250, 0.5);
  padding: 60px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}

.close-button {
  position: absolute;
  top: 33.3px;
  right: 29.47px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  width: 15.64px;
  height: 18.1px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-button:hover {
  opacity: 0.7;
}

.video-placeholder {
  width: 470px;
  height: 264px;
  background: #56A0D3;
  margin-bottom: 23px;
}

.content-section {
  display: flex;
  flex-direction: column;
  gap: 60px;
  height: 166px;
}

.intro {
  display: flex;
  flex-direction: column;
  gap: 30px;
  width: 475px;
}

.title {
  font-family: 'Oscine Trial', serif;
  font-weight: 300;
  font-size: 30px;
  line-height: 1.2em;
  color: #0C0931;
  margin: 0;
  width: 475px;
  height: 35px;
}

.description {
  font-family: 'Open Sans', sans-serif;
  font-weight: 300;
  font-size: 16px;
  line-height: 1.5em;
  color: #0C0931;
  margin: 0;
  width: 475px;
  height: 136px;
}

.cta-button {
  background: #1A76BC;
  color: #FFFFFF;
  border: none;
  border-radius: 6px;
  padding: 3px 15px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 600;
  font-size: 14px;
  line-height: 1.9285714285714286em;
  cursor: pointer;
  width: fit-content;
  height: fit-content;
  display: flex;
  align-items: center;
  gap: 15px;
}

.cta-button:hover {
  background: #145a94;
}

.cta-button:active {
  background: #0f4a7a;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .modal {
    width: 90vw;
    max-width: 595px;
    height: auto;
    max-height: 90vh;
    overflow-y: auto;
    padding: 40px;
  }
  
  .video-placeholder {
    width: 100%;
    height: 200px;
  }
  
  .intro,
  .title,
  .description {
    width: 100%;
  }
  
  .title {
    height: auto;
  }
  
  .description {
    height: auto;
  }
}
</style>
