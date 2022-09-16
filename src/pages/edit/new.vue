<script setup lang="ts">
    import { ref } from '@vue/reactivity'
    import card from '@/components/card.vue'
    const maison = ref({});
    </script>
    <template>
        <div>
            <div class="p-2">
                <h2>Résultat (Prévisualisation)</h2>
                <card v-bind="maison" />
            </div>
            <div class="p-2">
                <Formkit type="form" v-model="maison">
                    <Formkit name="nom" label="nom" />
                    <Formkit name="prix" label="prix" type="number" />
                    <Formkit name="favori" label="mettre en valeur "
                    type="checkbox" />

                </Formkit>

            </div>
        </div>
    </template>