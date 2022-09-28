<script setup lang="ts">
    import Card from "../components/card.vue";
    import {supabase} from "@/supabase";
    // let {data: maisons, error} = await supabase.from("maisons").select("*")
    console.log("Supabase:",supabase)
    const maisons = []
    // const {data: maisons, error} = await supabase.from("maisons").select("*")
</script> 
<template>
    <div v-for="maison in maisons" :key="maison.nom">
        <Card v-bind="maison"/>
    </div>
</template>