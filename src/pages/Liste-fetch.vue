<script setup>
    import Card from "../components/card.vue"
    const res = await fetch(maisons.json)
    const posts = await res.json()
</script>
<template>
    <Card/>
</template>