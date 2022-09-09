<script setup lang="ts">
    import Card from "../components/card.vue";
    const res = await fetch(maisons.json)
    const posts = await res.json()
</script>
<template>
    <Card v-for="maison in maisons" :key="maison.nom" v-bind="maison"/>
</template>