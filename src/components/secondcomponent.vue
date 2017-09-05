<template>
  <div class="hello">
    <h4>这是子组件</h4>
    <p>这是<span>来自父组件</span>的数据：{{myMessages}}</p>
    <input type="text" v-model="myMessages" disabled placeholder="disabled"/>
  </div>
</template>

<script>
export default {
  name: 'child',
  props: [
    'myMessages',//传递的值是这个
  ],
   mounted(){
     //console.log("子组件打印:","="+this.myMessages);
   }
}
</script>

<style scoped>
  .hello{
    margin-top: 30px;
  }
  h4,p{
    color: #41b883;;
    text-align: left;
    font-size: 20px;
  }
  p{
    font-size: 12px;
  }
  span{
    color: #35495e;
  }
</style>

