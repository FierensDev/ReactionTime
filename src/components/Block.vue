<template>
  <div v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock : false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        console.log(this.delay);
        setTimeout(() => {
            this.showBlock=true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>









<style scoped>
    div {
        clip-path: polygon(0% 15%, 15% 15%, 15% 0%, 85% 0%, 85% 15%, 100% 15%, 100% 85%, 85% 85%, 85% 100%, 15% 100%, 15% 85%, 0% 85%);
        background: #b55656;
        width: 200px;
        height: 200px;

        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>