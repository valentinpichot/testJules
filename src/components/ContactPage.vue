<template>
  <section class="contact-page fade-in" ref="contactPage">
    <div class="container">
      <h2>Contact Us</h2>
      <div class="contact-info">
        <div class="contact-form">
          <form>
            <input type="text" placeholder="Your Name" />
            <input type="email" placeholder="Your Email" />
            <textarea placeholder="Your Message"></textarea>
            <button type="submit">Send Message</button>
          </form>
        </div>
        <div class="contact-details">
          <h3>Our Address</h3>
          <p>123 Main Street, Anytown, USA 12345</p>
          <h3>Phone</h3>
          <p>(123) 456-7890</p>
          <h3>Social Media</h3>
          <div class="social-links">
            <a href="#">Facebook</a>
            <a href="#">Twitter</a>
            <a href="#">LinkedIn</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';

export default defineComponent({
  name: 'ContactPage',
  setup() {
    const contactPage = ref<Element | null>(null);

    onMounted(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              observer.unobserve(entry.target);
            }
          });
        },
        {
          threshold: 0.1,
        }
      );

      if (contactPage.value) {
        observer.observe(contactPage.value);
      }
    });

    return {
      contactPage,
    };
  },
});
</script>

<style scoped>
.contact-page {
  padding: 100px 0;
  background-color: #fff;
}

.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 20px;
}

h2 {
  font-size: 2.5rem;
  margin-bottom: 40px;
  text-align: center;
}

.contact-info {
  display: flex;
  justify-content: space-between;
}

.contact-form {
  flex: 1;
  margin-right: 40px;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.contact-form button {
  width: 100%;
  padding: 15px;
  background-color: #333;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.contact-details {
  flex: 1;
}

.social-links a {
  margin-right: 10px;
  color: #333;
  text-decoration: none;
}

@media (max-width: 768px) {
  .contact-info {
    flex-direction: column;
  }

  .contact-form {
    margin-right: 0;
    margin-bottom: 40px;
  }
}

@media (max-width: 480px) {
  .contact-page {
    padding: 60px 20px;
  }

  h2 {
    font-size: 2rem;
  }
}
</style>
