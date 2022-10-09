<template>

  <div>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
    <div class="pinkblock" v-if="showRedBlock" @click="clickTooSoon">
        <b>Prepare to Click</b>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            showRedBlock: true,
            timer: null,
            reationTime: 0,
        }
    },
    mounted() {
        setTimeout(()=>{
            this.showBlock = true
            this.showRedBlock = false
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reationTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reationTime)
        },
        clickTooSoon () {
            clearInterval(this.timer)
            this.$emit('end', this.reationTime)
        }
    }
}
</script>

<style scoped>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
    .pinkblock {
        width: 400px;
        border-radius: 20px;
        background: pink;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>