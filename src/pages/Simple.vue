<script setup lang="ts">
import card from "../components/Card.vue";


const obj = {
    NomMaison:"Faulkner Ave", PrixMaison:20, Image:"/Mask Group3.jpg", nbrSDB:2
}
const obj2 = {NomMaison:"Palm Harbor", PrixMaison:20, Image:"/Mask Group2.png", nbrSDB:2}
const obj3 = {NomMaison:"Beverly Springfield", PrixMaison:20, Image:"/Mask Group.png", nbrSDB:2}
</script>
<template>
    <h2>Page simple</h2>
    <div class="grid grid-flow-row-dense grid-cols-[repeat(auto-fit,minmax(345px,1fr))] gap-8 m-10 ">
        <card v-bind ="obj3" />
        <card v-bind ="obj2" />
        <card v-bind = "obj"/>
    </div>
</template>