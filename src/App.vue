<template>
  <nav>
    <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul>
      <li>
        <router-link class="text-red-600 underline" to="/">
          Accueil
          
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/Simple">
          Page simple
          
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/Liste">
          liste     
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/Liste-fetch">
          liste Fetch     
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/1">
          Liste Nombre     
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/new">
          New  
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/Liste-supabase">
          Supabase  
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/logout">
          login avec Github 
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/logIn">
          logIn  
        </router-link>
      </li>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="m-2 border-2 p-2" />
  </Suspense>

  <footer1 />
  
</template>

<script setup lang="ts">
import { Bars3Icon } from '@heroicons/vue/20/solid'
import footer1 from "./components/Footer.vue"

</script>
