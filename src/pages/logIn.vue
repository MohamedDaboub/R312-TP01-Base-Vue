<script setup lang="ts">
import { ref } from "@vue/reactivity";
import { supabase, user } from "../supabase";

async function signIn(data, node) {
  const { user, error } = await ( nvlUtilisateur.value
    ? supabase.auth.signUp(data)
    :  supabase.auth.signIn(data));
    console.log(user, error);
  if (error) {
    console.error(error);
    node.setErrors([error.message]);
  }
}
const nvlUtilisateur = ref(false);
</script>
<template>
  <div class="bg-blue-300 w-full">
    <button v-if="user" @pointerdown="supabase.auth.signOut()">
      Se déconnecter ({{ user.email }})
    </button>
    <FormKit
      v-else
      type="form"
      :submit-label="nvlUtilisateur ? 'S\'inscrire' : 'Se connecter'"
      @submit="signIn"
      :submit-attrs="{ classes: { input: 'bg-blue-900 px-6 justify-center w-full   py-4 text-white flex my-4 centre rounded' }}">
      <FormKit name="email" label="Votre email" type="email" wrapper-class="text-xl w-full " />
      <FormKit name="password" label="Mot de passe" type="password" wrapper-class="text-xl w-full " />
      <formKit
        label="Nouvel utilisateur ?"
        name="nvlUtilisateur"
        type="checkbox"
        v-model="nvlUtilisateur"
        wrapper-class="w-full flex py-4 text-xl "
      />
    </FormKit>
  </div>
</template>