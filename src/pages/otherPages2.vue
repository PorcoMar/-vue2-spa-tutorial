<template>
  <div class="container">
  	<swiper :params="swiperParams" :Pages="Pages" v-on:slide="slider" v-on:onTap="onTap"></swiper>
  	<p v-if="pagesA">pages is {{pagesA}}</p>
  	<p v-show="pagesB">click show {{pagesB}}</p>
		

  </div>
</template>


<script>
	 import swiper from '../components/swiper.vue'

	 export default {
	 		//el:'#app',
			data () {
				return {
					parentMsg: '子组件传递信息给父元素',
					pagesA:'',
					pagesB:'',
					calen:'-',
					plusn:'+',
					swiperParams:{
						  currentPage: 0,//当前页码
				          thresholdDistance: 100,//滑动判定距离
				          thresholdTime: 200,//滑动判定时间
				          autoplay:2000,//自动滚动[ms]
				          loop:true,//循环滚动
				          direction:'horizontal',//方向设置，垂直滚动 vertical
				          infinite:1,//无限滚动前后遍历数
				          effect:'fade', //slide fade
				          slidesToScroll:1,//一次翻几页
				          timingFunction: 'ease', //linear ease
				          duration: 300,//过度持续时间
					},
					Pages:[
				          {
				            title: 'slide1',
				            style:{
				             background:'url(http://www.haoniangjia.cn/img/new1.png)'
				            }
				          },
				          {
				           title: 'slide2',
				           style:{
				            background:'url(http://www.haoniangjia.cn/img/new2.png)'
				            }
				          },
				          {
				            title: 'slide3',
				            style:{
				              background:'url(http://www.haoniangjia.cn/img/up.png)',
				            },
				          }
				        ]
				}
			},
			methods: {
				
				slider:function(arg){
					console.log(arg)
					this.pagesA = arg; 
					
				},
				onTap:function(arg){
					console.log('onTap pages is : ',arg)
					this.pagesB = arg
				}

			},
	    components: {
				 swiper
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
