<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'
import {ref} from 'vue'

const menuIsOpen = ref(false)



onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
</script>

<template>
  <header>
    <button @pointerdown="menuIsOpen = !menuIsOpen"
    aria-controls="mainNav"
    aria-expanded="true"
    class="bg-indigo-500 rounded-lg p-2 text-white bg-sky-500/100 hover:bg-cyan-600 text-center leading-5 border-orange-950"
  >
    menu
  </button>
  <Transition
    class="transition-transform duration-1000"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="-translate-x-full"
  >
  <nav id="mainNav" v-show="menuIsOpen">
    <ul class="bg-emerald-200 text-center">
      <li class="decoration-double"><RouterLink to="/index" > Accueil </RouterLink></li>
      <li ><RouterLink to="/accordeon" > Accordeon </RouterLink></li>
      <li ><RouterLink to="/boucle_sur_donnees" > Boucle sur données </RouterLink></li>
    </ul>
  </nav>
</Transition>
        
        
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
