<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container">
      <div class="logo">
        <a href="#" @click.prevent="scrollTo('#home')">MyCompany</a>
      </div>
      <div class="menu-toggle" @click="toggleMenu">
        <div class="hamburger"></div>
      </div>
      <div class="nav-links" :class="{ open: isMenuOpen }">
        <ul>
          <li><a href="#home" @click.prevent="scrollTo('#home')">Home</a></li>
          <li><a href="#about" @click.prevent="scrollTo('#about')">About</a></li>
          <li><a href="#free-zone" @click.prevent="scrollTo('#free-zone')">Free Zone</a></li>
          <li><a href="#contact" @click.prevent="scrollTo('#contact')">Contact</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onUnmounted } from 'vue';

export default defineComponent({
  name: 'Navbar',
  setup() {
    const isMenuOpen = ref(false);
    const isScrolled = ref(false);

    const toggleMenu = () => {
      isMenuOpen.value = !isMenuOpen.value;
    };

    const scrollTo = (selector: string) => {
      const element = document.querySelector(selector);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
        isMenuOpen.value = false; // Close the menu after clicking a link
      }
    };

    const handleScroll = () => {
      isScrolled.value = window.scrollY > 50;
    };

    onMounted(() => {
      window.addEventListener('scroll', handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll);
    });

    return {
      isMenuOpen,
      isScrolled,
      toggleMenu,
      scrollTo,
    };
  },
});
</script>

<style scoped>
.navbar {
  background-color: transparent;
  color: white;
  padding: 1rem;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 1000;
  transition: background-color 0.7s ease-in-out;
}

.navbar.scrolled {
  background-color: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(10px);
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo a {
  color: white;
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: bold;
}

.nav-links ul {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
}

.nav-links li {
  margin-left: 20px;
}

.nav-links a {
  color: white;
  text-decoration: none;
}

.menu-toggle {
  display: none;
  cursor: pointer;
}

.hamburger {
  width: 25px;
  height: 3px;
  background-color: white;
  position: relative;
  transition: background-color 0.3s;
}

.hamburger::before,
.hamburger::after {
  content: '';
  position: absolute;
  width: 25px;
  height: 3px;
  background-color: white;
  transition: transform 0.3s;
}

.hamburger::before {
  top: -8px;
}

.hamburger::after {
  bottom: -8px;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .nav-links {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #333;
    width: 100%;
    padding: 1rem 0;
  }

  .nav-links.open {
    display: block;
  }

  .nav-links ul {
    flex-direction: column;
    align-items: center;
  }

  .nav-links li {
    margin: 10px 0;
  }
}
</style>
