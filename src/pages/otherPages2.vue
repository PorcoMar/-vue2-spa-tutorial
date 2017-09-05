<template>
  <div class="container">

		<!-- 这是父组件内容 -->
    <h4>子组件数据传递给父组件</h4>
	  <p>方式：用自定义事件</p>
	  <p class="text-center parent-tit">这是父组件</p>
		<!-- 父组件可以在使用子组件的地方直接用 v-on 来监听子组件触发的事件。 -->
		<h2 class="text-center">{{ totaler }}</h2>


		<!-- 这是子组件内容  子组件名字自定义 这个标签也用这个名字-->
		<div class="text-center">
			<p>这是子组件</p>
			<buttonCounter v-on:increment="plus"></buttonCounter>
		  <buttonCounter v-on:increment="cale"></buttonCounter>
		</div>

  </div>
</template>

<script>
	 import buttonCounter from '../components/thirdcomponent.vue'

	 export default {
			data () {
				return {
					parentMsg: '子组件传递信息给父元素',
					totaler: 10
				}
			},
			methods: {
			  plus: function () {
			    this.totaler += 1
			  },
			  cale: function () {
			    this.totaler -= 1
			  }
			},
	    components: {
	   	  buttonCounter
	    }
	 }
</script>

<style scoped>
	.parent-tit{
		margin-top: 30px;
	}
  h4{
  	font-size: 20px;
  }
  h2{
  	margin: 0 0 40px;
  }
  .text-center p {
  	color: #41b883;
  }
</style>
