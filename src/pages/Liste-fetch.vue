<script setup lang="ts">
    import Card from "../components/card.vue";
    const res = await fetch("maisons.json")
    const maisons = await res.json()
</script>
<template>
    <div v-for="maison in maisons" :key="maison.nom">
        <Card v-bind="maison"/>
    </div>
</template>