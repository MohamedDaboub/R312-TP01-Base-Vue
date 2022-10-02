<template>
  <nav class="bg-blue-900 text-white">
    <h4 class="text-xl flex justify-center py-5">
      <!-- <Bars3Icon class="inline-block h-5 w-5 text-blue-500" /> -->
      <!-- menu (dans <code class="font-mono">/src/App.vue</code>) -->
      TP Mohamed Daboub R312 
    </h4>
    <ul class=" flex gap-10 justify-center   uppercase border-b-2 border-indigo-300 py-4">
      <li>
        <router-link class="text-white " to="/">
          Accueil
          
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/Simple">
          Page simple
          
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/Liste">
          liste     
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/Liste-fetch">
          liste Fetch     
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/1">
          Liste Nombre     
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/edit/new">
          New  
        </router-link>
      </li>
      <li>
        <router-link class=" text-white " to="/Liste-supabase">
          Supabase  
        </router-link>
      </li>
      <li>
        <router-link class=" text-white " to="/logout">
          login avec Github 
        </router-link>
      </li>
      <li>
        <router-link class=" text-white " to="/logIn">
          logIn  
        </router-link>
      </li>
      <li>
        <router-link class="text-white " to="/quartier/quartier">
          quartier  
        </router-link>
      </li>
      <li>
        <router-link class="text-white" :to="{
          name: 'quartier-id',
          params: { id: 'quartierObject.code_quartier' },
        }">quartier ID</router-link>
      </li>
      <!-- <li>
        <router-link 
        :to="{ name: 'quartier-id', params: { id: quartierObject.code_quartier }, }"
        >{{ quartierObject.lebelle_quartier }}</router-link>
      </li> -->
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
import {supabase} from "./supabase";

</script>
