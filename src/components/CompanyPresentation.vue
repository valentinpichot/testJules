<template>
  <section class="company-presentation fade-in" ref="companyPresentation">
    <div class="container">
      <h2 ref="h2">About Our Company</h2>
      <p ref="p">
        We are a team of passionate individuals dedicated to creating elegant and engaging digital experiences. Our focus is on quality, innovation, and user satisfaction. We believe in the power of technology to transform businesses and connect people.
      </p>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import { gsap } from 'gsap';

export default defineComponent({
  name: 'CompanyPresentation',
  setup() {
    const companyPresentation = ref<Element | null>(null);
    const h2 = ref<Element | null>(null);
    const p = ref<Element | null>(null);

    onMounted(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              gsap.from([h2.value, p.value], {
                opacity: 0,
                y: 20,
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

      if (companyPresentation.value) {
        observer.observe(companyPresentation.value);
      }
    });

    return {
      companyPresentation,
      h2,
      p,
    };
  },
});
</script>

<style scoped>
.company-presentation {
  padding: 100px 0;
  background-color: #f8f8f8;
}

.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 20px;
}

h2 {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

p {
  font-size: 1.2rem;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .company-presentation {
    padding: 80px 20px;
  }

  h2 {
    font-size: 2rem;
  }

  p {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .company-presentation {
    padding: 60px 20px;
  }

  h2 {
    font-size: 1.8rem;
  }

  p {
    font-size: 1rem;
  }
}
</style>
