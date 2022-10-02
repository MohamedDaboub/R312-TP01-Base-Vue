<script setup lang="ts">
    import Card from "../components/card.vue";
    const res = await fetch("maisons.json")
    const maisons = await res.json()
</script>
<template>
    <div class="grid grid-flow-row-dense grid-cols-[repeat(auto-fit,minmax(330px,1fr))] gap-8 m-10 " v-for="maison in maisons" :key="maison.nom">
        <Card v-bind="maison"/>
    </div>
</template>