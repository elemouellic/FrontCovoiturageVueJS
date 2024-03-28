<script setup lang="ts">
import {ref} from 'vue';

// const router = useRouter()

// Tableau d'objets pour la navigation
const nav = [
  {name: 'Liste des trajets', to: '/tripslist'},
  {name: 'Rechercher un trajet', to: '/searchtrip'},
  {name: 'Vos trajets', to: '/yourtrips'},
  {name: 'Publier un trajet', to: '/publishtrip'},
  {name: 'Mon compte', to: '/account'},
  {name: 'Déconnexion', to: '/logout'}
]

// Variable pour gérer l'état du menu déroulant
const isOpen = ref(false);
</script>

<template>
  <nav class="bg-white border-gray-200 dark:bg-gray-900 dark:border-gray-700">
    <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
      <nuxt-link to="/" class="flex items-center space-x-3 rtl:space-x-reverse">
        <img src="/public/assets/logosvg.svg" class="h-8" alt="Logo"/>
        <span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white">Covoiturage Greta</span>
      </nuxt-link>
      <!-- Bouton pour ouvrir le menu -->
      <button @click="isOpen = !isOpen" class="lg:hidden">
        <span class="sr-only">Open main menu</span>
        <svg class="w-8 h-8" fill="none" stroke="white" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
        </svg>
      </button>
      <!-- Menu mobile -->
      <div v-if="isOpen" class="w-full block lg:hidden" id="navbar-dropdown-mobile">
        <ul class="flex flex-col font-medium p-4 mt-4 border border-gray-100 rounded-lg bg-gray-50 dark:bg-gray-800 dark:border-gray-700">
          <li v-for="(item, index) in nav" :key="index">
            <nuxt-link :to="item.to" class="block py-2 px-3 text-white rounded">{{ item.name }}</nuxt-link>
          </li>
        </ul>
      </div>
      <!-- Menu bureau -->
      <div class="hidden lg:block md:w-auto" id="navbar-dropdown-desktop">
        <ul class="flex flex-row font-medium space-x-8 dark:bg-gray-900 dark:border-gray-700">
          <li v-for="(item, index) in nav" :key="index">
            <nuxt-link :to="item.to" class="py-2 px-3 text-white rounded">{{ item.name }}</nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>

</style>