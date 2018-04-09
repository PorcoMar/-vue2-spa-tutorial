<template>
  <div>
    <p>this is news page,and understand is child components</p>
    <newsChildComponent :url_params="url_params"></newsChildComponent>
  </div>
</template>

<script>
  import newsChildComponent from '../components/newsChildComponent.vue';
  export default {
    data(){
      return{
        parentMsg:'',
        url_params:'https://api.github.com/search/code?q=addClass+in:file+language:js+repo:jquery/jquery'
      }
    },
    components:{
      newsChildComponent
    },
    methods:{

    }
  }
</script>
<style type="text/css">
  p{
    text-align:center;
  }
</style>