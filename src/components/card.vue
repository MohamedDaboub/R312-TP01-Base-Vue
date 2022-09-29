<script setup lang="ts">
import bath from "./Icons/Bathrooms.vue"
import heart from "./Icons/Heart.vue"
defineProps( {
    NomMaison: String,
    PrixMaison: Number,
    favori: Boolean,
    Image: String, // les images sont simplement l'URL absolue (depuis la racine, débute par '/' )
    nbrSDB: Number,
    size: String,
    nbrSDB1 : Number,

  })
</script>

<template>
   <figure class="flex flex-col bg-white mx-4">
     <!-- Pour changer la valeur d'un attribut on utilise un "binding" :
    https://vuejs.org/guide/essentials/template-syntax.html#attribute-bindings 
    Ici on affecte à l'attribut 'src' la 'props' "image"  -->
    <img class="rounded-t-lg mt-5 w-full " :src="Image" alt="" />
    <figcaption
      class="relative flex flex-col border-2 border-t-0 border-indigo-100"
    >
     <!-- Pour changer une classe CSS en fonction d'un booléen : 
      https://vuejs.org/guide/essentials/class-and-style.html#binding-html-classes -->
      <heart :class="{ 'fill-red-300': favori }" />

      <!-- Pour afficher du contenu textuel, simplement utiliser l'interpolation par double accolades (qui contiendront le JS dont l'interpretation donne le résultat affiché).  -->
      <div class="text-2xl font-bold text-indigo-500 pr-1">${{ PrixMaison }}</div>

      <h3 class="text-2xl text-gray-900">{{ NomMaison }}</h3>

      <hr class="border-indigo-100 border-t-2 my-4" />

      <div><bath class="inline-block pr-1" />{{ nbrSDB }} Bathrooms</div>
    </figcaption>
  </figure>

</template>