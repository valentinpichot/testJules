<template>
  <section class="free-zone fade-in" ref="freeZone">
    <div class="container">
      <h2 ref="h2">Free Zone</h2>
      <p ref="p">
        This is a flexible content area. You can add any content you want here, such as text, images, or even other components.
      </p>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import { gsap } from 'gsap';

export default defineComponent({
  name: 'FreeZone',
  setup() {
    const freeZone = ref<Element | null>(null);
    const h2 = ref<Element | null>(null);
    const p = ref<Element | null>(null);

    onMounted(() => {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
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
  .free-zone {
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
  .free-zone {
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
