<script setup>

import { ref, computed } from 'vue';

const props = defineProps({
  llistaContactes: {
    type: Array,
    required: true
  }
});

const cercaNom = ref('');

const contactesFiltrats = computed(() => {
  return props.llistaContactes.filter(contacte =>
    contacte.nom.toLowerCase().includes(cercaNom.value.toLowerCase())
  );
});

</script>

<template>
  <div>
    <h2>Cercar Contactes</h2>
    <input 
      type="text" 
      v-model="cercaNom" 
      placeholder="Cerca per nom" 
      class="field"
    />
    <ul>
      <li v-for="contacte in contactesFiltrats" :key="contacte.nom">
        <span class="contacte">{{ contacte.nom }}: <span class="tel">{{ contacte.telefon }}</span></span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 0.5rem;
}

a {
  text-decoration: none;
  color: #2e42ff;
}

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

.tel {
  color: #2e42ff;
}
</style>