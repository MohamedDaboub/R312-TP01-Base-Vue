<script setup lang="ts">
    import { ref } from '@vue/reactivity'
    import card from "./card.vue"
    const maison = ref({});
    </script>
<template>
    <div>
        <div class="p-2">
            <h2>Résultat (Prévisualisation)</h2>
            <card v-bind="maison" />
        </div>
        <div class="p-2">
            <FormKit type="form" v-model="maison" :submit-attrs="{ classes: { input: 'bg-blue-500 px-6   py-4 text-white flex my-4 centre     rounded' }}">
                <FormKit name="nom" label="nom" />
                <FormKit name="prix" label="prix" type="number"/>
                <FormKit name="favori" label="Mettre en valeur "
                type="checkbox"  wrapper-class="flex text-xl   " class="" />
            </FormKit>
        </div>
    </div>
</template>