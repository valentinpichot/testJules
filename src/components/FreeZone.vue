<template>
  <section class="free-zone" ref="freeZone">
    <div class="container">
      <h2 ref="h2">Free Zone</h2>
      <p ref="p">
        This is a flexible content area. You can add any content you want here, such as text, images, or even other components.
      </p>
      <SwiperSlider />
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import { gsap } from 'gsap';
import SwiperSlider from './SwiperSlider.vue';

export default defineComponent({
  name: 'FreeZone',
  components: {
    SwiperSlider,
  },
  setup() {
    const freeZone = ref<Element | null>(null);
    const h2 = ref<Element | null>(null);
    const p = ref<Element | null>(null);

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
              observer.unobserve(entry.target);
            }
          });
        },
        {
          threshold: 0.1,
        }
      );

      if (freeZone.value) {
        observer.observe(freeZone.value);
      }
    });

    return {
      freeZone,
      h2,
      p,
    };
  },
});
</script>

<style scoped>
.free-zone {
  padding: 120px 0;
  background-color: var(--secondary-color);
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
  .free-zone {
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
  .free-zone {
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
