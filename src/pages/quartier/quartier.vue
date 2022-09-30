<script setup lang="ts">
    import { Disclosure, DisclosureButton, DisclosurePanel,} from '@headlessui/vue'
    import { supabase } from "../../supabase";
    const { data, error } = await supabase.from("quartiercommune").select("*");
    if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
    import groupBy from "lodash/groupBy";
    </script>
    
    <template>
      <section class="flex flex-col">
        <h3 class="text-2xl">Liste des quartiers</h3>
            <!-- <li v-for="quartierObject in (data as any[])">
              {{ quartierObject.libelle_commune }} -
              {{ quartierObject.lebelle_quartier }}
            </li> -->
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
        
      </section>
</template>