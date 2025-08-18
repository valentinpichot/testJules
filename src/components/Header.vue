<template>
  <header class="video-header">
    <!--
      TODO: Replace this video with your own.
      The video is located in the `public` directory.
    -->
    <video src="/header-video.mp4" autoplay loop muted playsinline class="video-bg"></video>
    <div class="video-overlay"></div>
    <div class="header-content">
      <h1>Welcome to Our Company</h1>
      <p>Elegance and Engagement</p>
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Header',
});
</script>

<style scoped>
.video-header {
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  overflow: hidden;
}

.video-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.video-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.header-content {
  position: relative;
  z-index: 1;
}

@media (max-width: 768px) {
  .header-content h1 {
    font-size: 2rem;
  }

  .header-content p {
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .header-content h1 {
    font-size: 1.5rem;
  }

  .header-content p {
    font-size: 0.9rem;
  }
}
</style>
