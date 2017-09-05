<template>
  <div class="container">
  	<div class="app-head">
  		<div class="app-header-inner">
  			<router-link :to="'/'">
  				<img src="../assets/logo.png"/>
  			</router-link>
  			<div class="fr">
  				<ul class="nav-list">
  					<li>{{ userName }}</li>
  					<li @click="login" v-if="userName === ''">登录</li>
  					<li v-if="userName !== ''">|</li>
  					<li v-if="userName !== ''">退出</li>
  					<li v-if="userName === ''">|</li>
  					<li @click="ceshi" v-if="userName === ''">注册</li>
  					<li>|</li>
  					<li>关于</li>
  				</ul>
  			</div>
  		</div>
  	</div>
  	<div class="app-container">
  		<router-view></router-view>
  	</div>
  	<div class="app-footer">
  		<p>desgin By Yuji</p>
  	</div>
  	<my-dialog :show-model="showLoginModel"></my-dialog>
  </div>
</template>

<script type="text/babel">
import Dialog from './base/dialog'
export default {
	components: {
		MyDialog: Dialog
	},
  data () {
  	return {
  		userName: "",
      showLoginModel:false
  	}
  },
  methods: {
    ceshi () {
      this.$http.post('/api/standardized/userManage/adminList.htm',
        {
          "pageSize":"20",
          "pageNum":"1",
        }
      ).then(response => {
        // success callback
        console.log(response)
      }, response => {
        // error callback
        console.log(response)
      });
    },
    login () {
      this.$http.post('/api/u/login.htm',
        {
          "loginName":"10000006666",
          "passwd":"8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92"
        }
      ).then(response => {
        // success callback
        console.log(response)
      }, response => {
        // error callback
        console.log(response)
      });
    }
  }
}
</script>
 
<style>
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
a {
  color: inherit;
  text-decoration: none;
}
html{
	width: 100%;
	height: 100%;
}
body {
  background: #f0f2f5;
  font-family: "Helvetica Neue",Helvetica,Arial,"Hiragino Sans GB","Hiragino Sans GB W3","Microsoft YaHei UI","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
  font-size: 14px;
  color: #444;
  height:100%;
}
.container{
	height: 100%;
}
.fr{
	float: right;
}
.fl{
	float: left;
}
.app-head{
	height:80px;
	background: #363636;
	line-height: 80px;
	width: 100%;
	color:#b2b2b2;
}
.app-header-inner{
	width: 980px;
	height: 100%;
	margin: 0 auto;
	clear: both;
}
.app-header-inner img{
	width: 50px;
	margin-top: 15px;
}
.nav-list{
	overflow: hidden;
}
.nav-list li{
	float: left;
	cursor: pointer;
	padding:0 5px;
}
.app-container{
	min-height: calc(100% - 160px);
	width: 980px;
	margin: 0 auto;
}

.app-footer{
	height: 80px;
	background: #333;
	line-height: 80px;
	color: #fff;
	text-align: center;
	
}




</style>
