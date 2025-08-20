<template>
  <div v-if="isOpen" class="modal-overlay" @click="closeModal">
    <div class="modal" @click.stop>
      <!-- Close Button -->
      <button class="close-button" @click="closeModal">×</button>

      <!-- Video Area: placeholder -> video on CTA click -->
      <div class="video-area">
        <video
          v-if="showVideo"
          ref="videoRef"
          class="video"
          width="470"
          height="264"
          controls
          autoplay
          playsinline
        >
          <source src="/rickroll.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
        <div v-else class="video-placeholder"></div>
      </div>

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
import { ref, nextTick } from 'vue'
const showVideo = ref(false)
const videoRef = ref(null)

const closeModal = () => {
  // reset on close
  showVideo.value = false
  if (videoRef.value) {
    try {
      videoRef.value.pause()
      videoRef.value.currentTime = 0
    } catch (e) {}
  }
  emit('close')
}

const handleCtaClick = async () => {
  showVideo.value = true
  await nextTick()
  if (videoRef.value) {
    try {
      videoRef.value.muted = false
      videoRef.value.volume = 1
      await videoRef.value.play()
    } catch (e) {
      // Ignore autoplay restrictions errors
    }
  }
  emit('cta-click')
}
</script>

<style scoped>
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
  top: 15px;
  right: 15px;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 24px;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #0C0931;
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

.video-area {
  width: 470px;
  height: 264px;
  margin-bottom: 23px;
}

.video {
  width: 470px;
  height: 264px;
  display: block;
  background: #000;
  border: none;
  outline: none;
}

.content-section {
  display: flex;
  flex-direction: column;
  gap: 60px;
}

.intro {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.title {
  font-family: Arial, sans-serif;
  font-weight: 300;
  font-size: 30px;
  line-height: 1.2em;
  color: #0C0931;
  margin: 0;
}

.description {
  font-family: Arial, sans-serif;
  font-weight: 300;
  font-size: 16px;
  line-height: 1.5em;
  color: #0C0931;
  margin: 0;
}

.cta-button {
  background: #1A76BC;
  color: #FFFFFF;
  border: none;
  border-radius: 6px;
  padding: 3px 15px;
  font-family: Arial, sans-serif;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  width: fit-content;
  height: fit-content;
}

.cta-button:hover {
  background: #145a94;
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
}
</style>
