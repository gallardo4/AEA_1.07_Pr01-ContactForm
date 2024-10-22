<script setup>

import { ref } from 'vue';

const nouContacte = ref({
  nom: '',
  telefon: ''
});

const emitContacte = defineEmits(['contacte-afegit']);

const afegirContacte = () => {
  if (nouContacte.value.nom && nouContacte.value.telefon) {
    const contacteAEmetre = { nom: nouContacte.value.nom, telefon: nouContacte.value.telefon };
    emitContacte('contacte-afegit', contacteAEmetre);
    
    // Netejar els camps després d'afegir el contacte
    nouContacte.value.nom = '';
    nouContacte.value.telefon = '';
  }
};

</script>

<template>
  <div>
    <h2>Afegir Contactes</h2>
    <form @submit.prevent="afegirContacte">
      <input 
        type="text" 
        v-model="nouContacte.nom" 
        placeholder="Nom del contacte" 
        required 
        class="field"
      />
      <input 
        type="tel" 
        v-model="nouContacte.telefon" 
        placeholder="Telèfon del contacte" 
        required 
        class="field"
      />
      <button type="submit">Afegir Contacte</button>
    </form>
  </div>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

button {
  margin-top: 1rem;
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
</style>