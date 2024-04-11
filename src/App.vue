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
    class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  >
    menu
  </button>
  <nav id="mainNav">
    <ul>
      <li v-show="menuIsOpen"><RouterLink to="/" class="text-red-500 underline" > Accueil </RouterLink></li>
      <li v-show="menuIsOpen"><RouterLink to="/" > Page 2 </RouterLink></li>
      <li v-show="menuIsOpen"><RouterLink to="/" > Page 3 </RouterLink></li>
    </ul>
  </nav>
        
        
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
