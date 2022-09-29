<script setup lang="ts">
    import { ref } from '@vue/reactivity'
    import card from "./card.vue"
    const maison = ref({Image:'/Mask Groupe3.jpg',});
    </script>
<template>
    <div>
        <div class="p-2">
            <h2>Résultat (Prévisualisation)</h2>
            <card v-bind="maison" />
        </div>
        <div class="p-2">
            <FormKit type="form" v-model="maison" :config="{
                        classes: {
                                    input: 'p-2 rounded border-gray-300 shadow-sm border bg-bleu-300 hover:border-2 hover:black',
                                    label: 'text-black',
                                },
                    }"
            :submit-attrs="{ classes: { input: 'bg-blue-900 px-6 justify-center   py-4 text-white flex my-4 centre rounded' }}">
                <FormKit name="NomMaison" label="NomMaison" wrapper-class="text-xl  " />
                <FormKit name="PrixMaison" label="PrixMaison" type="number" wrapper-class="text-xl  "/>
                <div class="flex gap-5">
                    <FormKit name="nbrSDB" label="nbrSDB" type="number"/>
                </div>
                <FormKit name="favori" label="Mettre en valeur "
                type="checkbox"  wrapper-class="flex text-xl   " class="" />
            </FormKit>
        </div>
    </div>
</template>