<script setup lang ="ts">
  import { supabase } from "@/supabase";
  import { ref } from "@vue/reactivity";
  import { useRouter } from "vue-router";
  import { label } from "@formkit/inputs";
  import groupBy from "lodash/groupBy";
  const { data,} = await supabase.from("quartiercommune").select("*");
  const router = useRouter();
  const quartier = ref({});
  const props = defineProps(["id"]);
  if (props.id) {
    let { data, error } = await supabase
      .from("quartier")
      .select("*")
      .eq("id_quartier", props.id);
    if (error)  console.log("n'a pas pu charger le table Quartier :", error);
    else quartier.value = data[0];
  }
    const { data: QuartierCommune, error } = await supabase
  .from("quartier")
  .select("*");
  if (error) console.log("n'a pas pu charger la vue quartiercommune :", error);

  async function upsertquartiercommune(dataForm, node) {
    const { data, error } = await supabase.from("quartier").upsert(dataForm);
    if (error)  node.setErrors([error.message]);
    else {
      node.setErrors([]);
      router.push({ name: "quartier-id", params: { id: data[0].id_quartier } });
    }
  }
  async function supprimerQuartier() {
    const { data, error } = await supabase
      .from("quartier")
      .delete()
      .match({ codequartier: quartier.value.code_quartier });
    if (error) {
      console.error(
        "Erreur à la suppression de ",
        quartier.value,
        "erreur :",
        error
      );
    } else {
      router.push("/quartier/quartier");
    }
  }  
  const { data: listeCommune, } = await supabase
    .from("Commune")
    .select("*");
  if (error) console.log("n'a pas pu charger la table Commune :", error);
  const optionsCommune = listeCommune?.map((Commune) => ({
    value: Commune.code_commune,
    label: Commune.libelle_commune,
  })
  
  );
  
  </script>
  <template>
    <div class="bg-blue-900 text-white">
      <div class="p-2 ">
        <h2 class="text-2xl py-4 "> Resulat (Prévisualisation)</h2>
        <div>
          <Disclosure v-for="(listequartier, libellecommune) in groupBy( data, 'libelle_commune' )" :key="libellecommune" >
            <DisclosureButton >{{ libellecommune}}</DisclosureButton>
              <DisclosurePanel>
                <ul>
                  <li v-for="quartierObject in listequartier" :key="quartierObject.id">
                    {{ quartierObject.lebelle_quartier }}
                  </li>
                </ul>
              </DisclosurePanel> 
            </Disclosure>
        </div>
      </div>
      <div class="p-2 border-2 mt-20 bg-indigo-50 rounded-2xl text-black  ">
        <FormKit type="form" v-model="quartier" @submit="upsertquartiercommune"
          :submit-attrs="{ classes: { input: 'bg-blue-300 px-4 my-3 py-4  p-1 rounded' } }">
          <FormKit name="lebelle_quartier" label="Nom Quartier" :config="{
          classes: {
          input: 'p-2 rounded border-gray-300 shadow-sm border bg-bleu-300 hover:border-2 hover:black',
          label: 'text-black',
          },
          }" />
          <FormKit type="select" name="code_Commune" label="Commune" :options="optionsCommune" :config="{
          classes: {
          input: 'p-2 rounded border-gray-300 shadow-sm border bg-bleu-300 hover:border-2 hover:black my-2',
          label: 'text-black',
          },
          }" />
        </FormKit>
      </div>
      <div class="flex justify-between px-4 py-8 text-black">
      <button type="button"  v-if="quartier" @click="($refs.dialogSupprimer as any).showModal()"
        class="focus-style justify-self-end rounded-md bg-blue-300 px-8 py-4 shadow-sm">
        Supprimer l'offre
      </button>
        <button type="button" @click="router.push('/quartier/quartier')"
          class="focus-style justify-self-end rounded-md bg-blue-300 px-8 py-4 shadow-sm">
          Retour
        </button>
      </div>
      <div class="gap-4 flex">
        <dialog class="gap-4" ref="dialogSupprimer" @click="($event.currentTarget as any).close()">
          <button type="button" class="focus-style justify-self-end rounded-md bg-blue-300 px-8 py-4 shadow-sm">
            Annuler</button>
            <button type="button" @click="supprimerQuartier()"
            class="focus-style rounded-md bg-blue-300 px-8 py-4 shadow-sm">
            Confirmer suppression
          </button>
        </dialog>
      </div>
    </div>
  </template>