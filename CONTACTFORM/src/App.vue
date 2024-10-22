<script setup>
import { ref } from 'vue';
import AfegirContactes from './components/AfegirContactes.vue';
import CercarContactes from './components/CercarContactes.vue';

const llistaContactes = ref([]);

const afegirContacte = (nouContacte) => {
  llistaContactes.value.push(nouContacte);
};
</script>

<template>
  <main>
    <h1>Llibreta de Contactes</h1>
    <AfegirContactes @contacte-afegit="afegirContacte" />
    <CercarContactes :llistaContactes="llistaContactes" />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
