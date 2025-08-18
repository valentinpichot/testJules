<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
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
  background-color: var(--secondary-color);
  padding: 40px 0;
  border-top: 1px solid #e5e5e5;
}

.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.social-links a {
  margin-left: 20px;
  color: var(--text-color);
  text-decoration: none;
  font-weight: 600;
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
  }

  .social-links {
    margin-top: 20px;
  }

  .social-links a {
    margin: 0 10px;
  }
}
</style>
