<template>
  <div class="container-inner">
  	<div class="index-left">
  	  <div class="index-left-block">
  	  <h2>全部产品</h2>
  	  <h3>PC产品</h3>
  	  <ul>
  		<li v-for="item in profduct.list">
  		  <a :href="item.url">{{item.name}}</a>
  		</li>
  	  </ul>
  	  </div>
  	  <div class="index-left-block">
  	  	<h2>最新消息</h2>
  	  	
  	  </div>
  	</div>
  	<div class="index-right">
  	  <slide-show :slides="slideImgs"></slide-show>
  	</div>
  </div>
</template>

<script>
import slideShow from '../components/slideShow'
export default {
  name: 'indexPage',
  components: {
  	slideShow
  },
  data () {
    return {
      profduct: {
      	title: "全部产品",
      	list: [
      	  { name:"数据统计" , url:"http://www.baidu.com" },
      	  { name:"数据预测" , url:"http://www.baidu.com" },
      	  { name:"流量分析" , url:"http://www.baidu.com" },
      	  { name:"广告发布" , url:"http://www.baidu.com" },
      	]
      },
      slideImgs: [
        {
        	url:require('../assets/slideShow/pic1.jpg'),
        	tit:'第一张图片',
        	href: "http://www.xxx.com"
        },
        {
        	url:require('../assets/slideShow/pic2.jpg'),
        	tit:'第二张图片',
        	href: "http://www.xxx.com"
        },
        {
        	url:require('../assets/slideShow/pic3.jpg'),
        	tit:'第三张图片',
        	href: "http://www.xxx.com"
        },
        {
        	url:require('../assets/slideShow/pic4.jpg'),
        	tit:'第四张图片',
        	href: "http://www.xxx.com"
        }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container-inner {
  width:100%;
  overflow: hidden;
}
.index-left {
  width:300px;
  float: left;
  text-align: left;
}
.index-left-block{
  margin-top:10px;
  width: 100%;
  background: #fff;
}
.index-left-block h2{
  background: #4fc08d;
  padding: 10px 15px;
  width: 270px;
  box-shadow: 0 0 1px #ddd;
  color: #fff;
  margin-bottom: 15px;
}
.index-left-block h3{
  padding: 10px 15px;
  width: 100%;
  font-weight: 600;
}
.index-left-block ul{
  padding: 10px 15px;
  width: 100%;
}
.index-left-block ul li{
  padding: 5px ;
  width: 100%;
  cursor: pointer;
}
.index-left-block ul li:hover{
  color: #4fc08d;
}
.index-right {
  float: left;
  width: calc(100% - 322px);
  margin: 10px 0 15px 20px;
}
</style>
