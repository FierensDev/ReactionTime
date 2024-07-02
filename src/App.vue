<template>
  <h1>💥Improve your reaction time !🚀</h1>
  <button @click="start" :disabled="isPlaying">{{ score ? "Replay" : "Play" }}</button>
  
  <div class="components">
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Result v-if="score != null" :score="score"/>
  </div>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {

  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score : null
    }
  },
  methods: {
    start(){
      this.score = null
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #2c3e50;
  color: white;

  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 0;

  justify-items: center;
  align-items: center;

  width: 100%;
  height: 100vh;
}


h1{
  grid-column: 2/3;
}

button{
  background: #ffc6c6;
  width: 100px;
  height: 100px;
  border-radius: 20px;
  border: 3px solid red;
  font-size: 20px;

  grid-column: 2/3;
  grid-row: 2/3;
}

.components{
  grid-column: 2/3;
  grid-row: 3/3;
}
</style>
