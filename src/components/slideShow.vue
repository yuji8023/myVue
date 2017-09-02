<template>
  <div class="slide-show" @mouseover="clearInv" @mouseout="runInv">
  	<div class="slide-img">
  		<a :href="slides[nowIndex].href">
	  		<transition  name="slide-trans">
		  	    <img v-if="isShow" :src="slides[nowIndex].url" />
		  	</transition >
		  	<transition  name="slide-trans-old">
		  	    <img v-if="!isShow" :src="slides[nowIndex].url" />
		  	</transition >
		  </a>
  	</div>
  	<div class="slide-next" @click="go(nextIndex)"> &gt; </div>
  	<div class="slide-prev" @click="go(preIndex)"> &lt; </div>
  	<div class="tit-shadow">
  		<h2>{{slides[nowIndex].tit}}</h2>
  		<ul class="slide-radio">
  			<li @click="go(index)" :class="{on: index === nowIndex}" v-for="(item, index) in slides"></li>
  		</ul>
  	</div>
  	
  </div>
</template>

<script>
export default {
	props:{
		slides: {
			type: Array,
			default: []
		},
		inv: {
			type:Number,
			default: 3000
		}
	},
  name: 'hello',
  data () {
    return {
      nowIndex: 0,
      isShow: true
    }
  },
  computed: {
  	preIndex () {
  		if(this.nowIndex === 0){
  			return this.slides.length - 1
  		}else{
  			return this.nowIndex - 1
  		}
  	},
  	nextIndex () {
  		if(this.nowIndex === this.slides.length - 1){
  			return 0
  		}else{
  			return this.nowIndex + 1
  		}
  	}
  },
  methods: {
  	go (index) {
  		this.isShow = false;
  		setTimeout(() => {
  			this.isShow = true
  			this.nowIndex = index
  		},10)
  		
  	},
  	runInv () {
  		this.invid = setInterval(() =>{
  				this.go(this.nextIndex)
  			},this.inv)
  	},
  	clearInv () {
      clearInterval(this.invid)
    }
  },
  mounted () {
  	this.runInv();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.slide-show {
		width:100%;
		height: 370px;
		position: relative;
		overflow: hidden;
		border: 1px solid #333;
	}
	.slide-show h2 {
		position: absolute;
		color: #fff;
		height: ;
		padding-left: 20px;
	}
	.slide-radio {
		float: right;
		line-height: 40px;
		padding-top: 2px;
	}
	.slide-radio li{
		width: 12px;
		height: 12px;
		display: inline-block;	
		border:1px solid #fff;
		border-radius: 50%;
		margin-right: 20px;
	}
	.slide-radio li.on{
		width: 12px;
		height: 13px;
		border:none;
		background: #fff;
	}
	.tit-shadow {
		width: 100%;
		height: 40px;
		position:absolute;
		line-height: 40px;
		left: 0;
		bottom: 0;
		background: rgba(0 , 0 , 0 , 0.6);
	}
	.slide-img{
		
	}
	.slide-img img{
		width: 658px;
		position: absolute;
		top:0
	}
	.slide-next {
		font-size: 24px;
		width:40px;
		line-height: 50px;
		text-align: center;
		background: rgba(0 , 0 , 0 , 0.4);
		color: #fff;
		height: 50px;
		position: absolute;
		right: 0;
		top:calc(50% - 25px);
		cursor: pointer;
	}
	.slide-prev {
		font-size: 24px;
		width:40px;
		line-height: 50px;
		text-align: center;
		background: rgba(0 , 0 , 0 , 0.4);
		color: #fff;
		height: 50px;
		position: absolute;
		left: 0;
		top:calc(50% - 25px);
		cursor: pointer;
	}
	.slide-trans-enter-active {
	  transition: all .5s;
	}
	.slide-trans-enter {
	  transform: translateX(658px);
	}
	.slide-trans-old-leave-active {
	  transition: all .5s;
	  transform: translateX(-658px);
	}
</style>
