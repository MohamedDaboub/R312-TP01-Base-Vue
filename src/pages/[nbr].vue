<script setup lang="ts">
    import card from '../components/card.vue'
    const res = await fetch("maisons.json")
    const maisons = await res.json()
    defineProps<{nbr:String}>();
</script>

    <template>
        <div>
            <card v-bind="maisons[Number(nbr)]"/>
        </div>
    </template>