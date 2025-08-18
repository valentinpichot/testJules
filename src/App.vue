<template>
  <Navbar />
  <div id="home">
    <Header />
  </div>
  <div id="about">
    <CompanyPresentation />
  </div>
  <div id="free-zone">
    <FreeZone />
  </div>
  <div id="contact">
    <ContactPage />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Navbar from './components/Navbar.vue';
import Header from './components/Header.vue';
import CompanyPresentation from './components/CompanyPresentation.vue';
import FreeZone from './components/FreeZone.vue';
import ContactPage from './components/ContactPage.vue';
import { useLenis } from './composables/useLenis';

export default defineComponent({
  name: 'App',
  components: {
    Navbar,
    Header,
    CompanyPresentation,
    FreeZone,
    ContactPage,
  },
  setup() {
    useLenis();
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
