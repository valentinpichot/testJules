<template>
  <section class="contact-page fade-in" ref="contactPage">
    <div class="container">
      <h2 ref="h2">Contact Us</h2>
      <div class="contact-info">
        <div class="contact-form" ref="contactForm">
          <form>
            <input type="text" placeholder="Your Name" />
            <input type="email" placeholder="Your Email" />
            <textarea placeholder="Your Message"></textarea>
            <button type="submit">Send Message</button>
          </form>
        </div>
        <div class="contact-details" ref="contactDetails">
          <h3>Notre Adresse</h3>
          <p>123 Rue de la République, 75001 Paris, France</p>
          <h3>Téléphone</h3>
          <p>+33 1 23 45 67 89</p>
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
import { gsap } from 'gsap';

export default defineComponent({
  name: 'ContactPage',
  setup() {
    const contactPage = ref<Element | null>(null);
    const h2 = ref<Element | null>(null);
    const contactForm = ref<Element | null>(null);
    const contactDetails = ref<Element | null>(null);

    onMounted(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              gsap.from([h2.value, contactForm.value, contactDetails.value], {
                autoAlpha: 0,
                y: 10,
                duration: 0.5,
                stagger: 0.2,
              });
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
      h2,
      contactForm,
      contactDetails,
    };
  },
});
</script>

<style scoped>
.contact-page {
  padding: 120px 0;
  background-color: var(--background-color);
}

.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
}

h2 {
  font-size: 3rem;
  font-weight: 600;
  margin-bottom: 40px;
  text-align: center;
}

.contact-info {
  display: flex;
  justify-content: space-between;
}

.contact-form {
  flex: 1;
  margin-right: 60px;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 15px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-family: var(--font-family);
  font-size: 1rem;
}

.contact-form button {
  width: 100%;
  padding: 15px;
  background-color: var(--primary-color);
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 600;
}

.contact-details {
  flex: 1;
}

.contact-details h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 10px;
}

.contact-details p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 20px;
}

.social-links a {
  margin-right: 15px;
  color: var(--text-color);
  text-decoration: none;
  font-weight: 600;
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
</style>
