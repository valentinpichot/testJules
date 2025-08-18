<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="logo">
          <a href="#">MyCompany</a>
        </div>
        <p>&copy; 2025 MyCompany. All rights reserved.</p>
        <div class="social-links">
          <a href="#">Facebook</a>
          <a href="#">Twitter</a>
          <a href="#">LinkedIn</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Footer',
});
</script>

<style scoped>
.footer {
  background-color: #f5f5f7;
  padding: 60px 0;
  color: #6e6e73;
}

.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
  text-align: center;
}

.logo a {
  color: var(--text-color);
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 20px;
  display: inline-block;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.social-links {
  margin-top: 20px;
}

.social-links a {
  margin: 0 15px;
  color: #6e6e73;
  text-decoration: none;
  font-weight: 600;
}

.footer p {
  font-size: 0.9rem;
}
</style>
