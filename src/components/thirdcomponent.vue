<template>
    <div class="thirdComponent" >
      <button v-on:click="increment" :style="{background:color}">{{ counter }}</button>
    </div>
</template>

<script>
  export default {
    name: 'fuck',
    data () {
      return {
        counter: 0,color:'',
        number:0
      }
    },
    methods: {
      increment: function () {
        this.counter += 1
        this.counter1 = Math.floor(Math.random()*255)
        this.counter2 = Math.floor(Math.random()*255)
        this.counter3 = Math.floor(Math.random()*255)
        this.color=`rgb(${this.counter1},${this.counter2},${this.counter3})`
        this.$emit('increment')
      }
    }
  }
</script>

<style scoped>
  .thirdComponent{
    display: inline-block;
  }
  button{
    color: #41b883;
    border-color: #41b883;
  }
  .sacle{
    border:1px solid #ccc;display:flex;flex-direction:row;
  }
</style>