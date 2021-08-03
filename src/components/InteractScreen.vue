<template>
    <div class="screen">
        <CardFlip v-for="(card, index) in cardsContext" :key="index" :imgBackFaceUrl="`images/${card}.png`"/>
    </div>
</template>

<script>
import CardFlip from './Card.vue'
export default {
    name: 'InteractScreen',
    props: {
        cardsContext: {
            type: Array,
            default: function() {
                return [];
            }
        }
    },
    components: {
        CardFlip
    }
}
</script>

<style scoped>

</style>