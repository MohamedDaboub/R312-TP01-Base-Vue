<script setup lang="ts">
import card from "../components/Card.vue";

</script>
<template>
    <h2>Page simple</h2>
    <div class="grid grid-flow-row-dense grid-cols-[repeat(auto-fit,minmax(345px,1fr))] gap-8 m-10 ">
        <card nom="Beverly Springfield" prix="20" image="/Mask Group.png" nbrSDB="2" />
        <card nom="Palm Harbor" prix="20" image="/Mask Group2.png" nbrSDB="2" />
        <card nom="Faulkner Ave" prix="20" image="/Mask Group3.jpg" nbrSDB="2"/>
    </div>
</template>