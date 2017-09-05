<template>
<div>
  <h4 class="news-tit">上拉加载</h4>
  <div  v-for="(item, index) in listArr">
    <b class="liStyle">{{index}}----{{item.name}}</b>
  </div>
    <div id="loading" style="color:red;text-align:center;" v-if="loading">
            Loading...
    </div>
    <div style="height:50px;width:100%;"></div>
  </div>
</template>
<script>

import axios from 'axios'

export default {
  data (){
    return {
      loading:false,
      listArr:[],
      pageNo:1
    }
  },
  created() {
    this.loadList();
　　　　//监听滚动
    window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
      loadList() {
          this.loading = true;
          axios.get('https://api.github.com/search/code?q=addClass+in:file+language:js+repo:jquery/jquery', {
            params: {

            }
          })
          .then((response)=> {
            this.loading = false;
            this.listArr = response.data.items;
            console.log(this.listArr,"加载完成");
          })
          .catch((error)=> {
            console.log(error);
          });
      },
      
      loadMore(){
        console.log("pageNo="+this.pageNo)
          axios.get('https://api.github.com/search/code?q=addClass+in:file+language:js+repo:jquery/jquery', {
            params: {
              
            }
          })
          .then((response)=> {
            console.log(response.data.items)
            this.loading = false;
            this.listArr = this.listArr.concat(response.data.items);
          })
      },
      handleScroll() {
　　　　//判断滚动到底部
        //console.log($(window).scrollTop() ,$(document).height()-$(window).height())
        if ($(window).scrollTop() >=$(document).height() - $(window).height()) {
          this.loading = true;
          if(!this.isLoad){//isLoad是防止一次加载多条而做的防御工作
            this.isLoad = true;
            this.pageNo++;
            this.loadMore(this.pageNo); 
          }
          setTimeout(()=>{
            this.isLoad = false;
          },500)
        }
      }
  },
}
</script>

<style>
  .news-tit{
    font-size: 18px;
    margin-top: 60px;
    text-align: center;
    background:#ccc;
    height:30px;line-height:30px;
  }
  .liStyle{
    display:flex;height:100px;justify-content: center;align-items:center;border:1px dashed #ccc;
  }
</style>
