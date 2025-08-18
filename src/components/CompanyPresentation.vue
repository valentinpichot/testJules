<template>
  <section class="company-presentation" ref="companyPresentation">
    <div class="container">
      <h2 ref="h2">About Our Company</h2>
      <p ref="p">
        We are a team of passionate individuals dedicated to creating elegant and engaging digital experiences. Our focus is on quality, innovation, and user satisfaction. We believe in the power of technology to transform businesses and connect people.
      </p>
      <div class="cards">
        <div class="card" ref="card1">
          <div class="icon">ICON</div>
          <h3>Quality</h3>
          <p>We are committed to delivering high-quality products that meet the needs of our clients.</p>
        </div>
        <div class="card" ref="card2">
          <div class="icon">ICON</div>
          <h3>Innovation</h3>
          <p>We are constantly exploring new technologies and ideas to create innovative solutions.</p>
        </div>
        <div class="card" ref="card3">
          <div class="icon">ICON</div>
          <h3>Satisfaction</h3>
          <p>We work closely with our clients to ensure their satisfaction with our products and services.</p>
        </div>
      </div>
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
    const card1 = ref<Element | null>(null);
    const card2 = ref<Element | null>(null);
    const card3 = ref<Element | null>(null);

    onMounted(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              gsap.from([h2.value, p.value], {
                autoAlpha: 0,
                y: 10,
                duration: 0.5,
                stagger: 0.2,
              });
              gsap.from([card1.value, card2.value, card3.value], {
                autoAlpha: 0,
                y: 20,
                duration: 0.5,
                stagger: 0.2,
                delay: 0.4,
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
      card1,
      card2,
      card3,
    };
  },
});
</script>

<style scoped>
.company-presentation {
  padding: 120px 0;
  background-color: var(--secondary-color);
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 40px;
  margin-top: 60px;
}

.card {
  background-color: var(--background-color);
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.icon {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 20px;
}

.card h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 10px;
}

.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
  text-align: center;
}

h2 {
  font-size: 3rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

p {
  font-size: 1.25rem;
  line-height: 1.8;
  max-width: 800px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .company-presentation {
    padding: 100px 20px;
  }

  h2 {
    font-size: 2.5rem;
  }

  p {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .company-presentation {
    padding: 80px 20px;
  }

  h2 {
    font-size: 2rem;
  }

  p {
    font-size: 1rem;
  }
}
</style>
