<script setup lang="ts">
    import Card from "../components/card.vue";
    import {supabase} from "../supabase";
    // let {data: maisons, error} = await supabase.from("maisons").select("*")
    console.log("Supabase:",supabase)
    let { data: Maison, error } = await supabase
    .from('Maison')
    .select('*')

</script> 
<template>
    <Card v-for="maison in Maison" :key="maison.id" v-bind="maison"/>   
</template>