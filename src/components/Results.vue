<template>
    <div>
        <p v-if="score != 0">Reaction Time - {{ score }} ms</p>
        <p :class="{rank, warnning: score == 0}">{{ rank }}</p>
    </div>
</template>

<script>
export default {
    name:'Results',
    props: ['score'],
    data() {
        return{
            rank: null
        }
    },
    mounted() {
        if(this.score == 0){
            this.rank = 'Click too Soon'
        }else if(this.score < 250 && this.score > 0){
            this.rank = 'Super Sonic'
        }else if (this. score < 400){
            this.rank = 'Well Played'
        }else{
            this.rank = 'Slow as turtle'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
    .warnning {
        color: #cc4635;
    }
</style>