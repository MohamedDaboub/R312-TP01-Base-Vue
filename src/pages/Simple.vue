<script setup lang="ts">
import card from "../components/Card.vue";


const obj = {
    nom:"Faulkner Ave", prix:20, image:"/Mask Group3.jpg", nbrSDB:2
}
const obj2 = {nom:"Palm Harbor", prix:20, image:"/Mask Group2.png", nbrSDB:2}
const obj3 = {nom:"Beverly Springfield", prix:20, image:"/Mask Group.png", nbrSDB:2}
</script>
<template>
    <h2>Page simple</h2>
    <div class="grid grid-flow-row-dense grid-cols-[repeat(auto-fit,minmax(345px,1fr))] gap-8 m-10 ">
        <card v-bind ="obj3" />
        <card v-bind ="obj2" />
        <card v-bind = "obj"/>
    </div>
</template>