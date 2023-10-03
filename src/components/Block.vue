<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    CLICK ME FAST
  </div>
</template>

<script>
export default {
    props: ['delay', 'isPlaying'],
    data() {
        return {
            showBlock: false,
            reactionTime: 0,
            timer: null
        }
    },
    mounted() {
        setTimeout(()=>{this.showBlock = true, this.startTimer()}, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {this.reactionTime += 10}, 5)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('endG', this.reactionTime)
        }
    }

}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: greenyellow;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>