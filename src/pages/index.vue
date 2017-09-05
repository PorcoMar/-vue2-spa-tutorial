<template>
 <div>
   <input type="" v-model="content" autofocus="autofocus" placeholder="type something">
   <p>this.message == {{content}}</p>
   <contentComponent :my-messages="content"></contentComponent>
   <charge v-on:jian="jian1"></charge>
   <div>this.value=={{number}}</div>
 </div>
 
</template>

<script>
import contentComponent from '../components/secondcomponent.vue'
import charge from "../components/cacle.vue"
export default{
  data(){
    return {
      content:"",
      number:0
    }
  },
  created() {
    
  },
  methods:{
    jian1:function(){
      setTimeout(()=>{
        let value = $("#caleValue").text()
        //console.log(value)
        this.number = value
      })
 
    },
  },
  components:{
    contentComponent,
    charge
  }
}
</script>

<style>

</style>