<template>
    <div class="screen">
        <CardFlip
        v-for="(card, index) in cardsContext"
        :key="index"
        :imgBackFaceUrl="`images/${card}.png`"
        :card="card"
        @onFlip="checkkRule($event)"
        />
    </div>
</template>

<script>
import CardFlip from "./Card.vue";
export default {
    name: "InteractScreen",
    props: {
        cardsContext: {
        type: Array,
        default: function () {
            return [];
        },
        },
    },
    components: {
        CardFlip,
    },
    data() {
        return {
        rules: [],
        };
    },
    methods: {
        checkkRule(card) {
            if(this.rules.length === 2) return false;

            this.rules.push(card);
            if(this.rules.length === 2 && this.rules[0] === this.rules[1]){
                console.log("right...");
            }else if(this.rules.length === 2 && this.rules[0] !== this.rules[1]) {
                console.log("Wrong...");
                //close two card
                
                //reset rules to []
            }else {
                return false
            }
        },
    }
};
</script>

<style scoped>
</style>