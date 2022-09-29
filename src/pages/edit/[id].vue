<script setup lang="ts">
    import cardedit from "../../components/cardedit.vue";
    import { value supabase } from "../../supabase";
    defineProps({
      id: String,
    });
    const props = defineProps(["id"]);
    if (props.id) {
        // On charge les données de la maison
        let { data, error } = await supabase
        .from("Maison")
        .select("*")
        .eq("id", props.id);
        if (error) console.log("n'a pas pu charger le table Maison :", error);
        else Maison.value = (data as any[])[0];
}
</script>   
<template>
    <div>
        <p>Edit</p>
        <cardedit :id="id"/>
    </div>
</template>