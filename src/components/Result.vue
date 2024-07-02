<template>
  <p>Reaction time : {{ score }} ms</p>
</template>

<script>
export default {
    props: ['score']
}
</script>

<style scoped>
    p{
        font-size: 30px;
        background: red;
        color: white;
        padding: 20px;
        border: 3px solid white;
    }
</style>