<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'
import {ref} from 'vue'
const sectionOpen = ref(1)
onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
</script>

<template>
<section>
    <button class="text-xl" @pointerdown="sectionOpen=1">bouton 1</button>
    <p v-show="sectionOpen==1">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Maiores odio quas minima amet nam? Libero veritatis aliquam, dolore sequi ducimus fuga? Libero corporis iste hic quas ut deleniti necessitatibus distinctio.</p>
</section>
<section>
    <button class="text-xl" @pointerdown="sectionOpen=2">bouton 2</button>
    <p v-show="sectionOpen==2">Error ut assumenda ad accusamus fugiat labore vero amet velit dicta! Voluptates fugiat necessitatibus nostrum doloribus libero, earum cumque, corrupti adipisci blanditiis dolorem voluptate ab sunt accusamus impedit? Consequatur, excepturi!</p>
</section>
<section>
    <button class="text-xl" @pointerdown="sectionOpen=3">bouton 3</button>
    <p v-show="sectionOpen==3">Quasi, in at? Odit, harum. Nostrum numquam reprehenderit dicta natus eius delectus necessitatibus id dolor, ipsum, saepe nam odit. Ad mollitia et earum cum dolorem? Omnis repellat dolor saepe maiores!</p>
</section>
</template>