<template>
  <div v-if="showModel" class="model-shoadow">
    <div class="model-wrap">
      <div class="mode-close" @click="closeModel">X</div>
      <div class="model-content">
        <solt>hello</solt>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'dialog',
  props :{
    showModel :{
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.model-shoadow {
	position:fixed;
	left: 0;
	top: 0;
	width: 100%;
	height: 100%;
	background: rgba(0 ,0 ,0 ,0.3);
	z-index: 5;
}
.model-wrap {
  width: 40%;
  border: 2px solid #333;
  background: #fff;
  position: absolute;
  left: calc(50% - 20%);
  top: 200px;
  line-height: 1.5;
  padding: 20px 10px 10px;
}
.mode-close {
  position: absolute;
  right: 15px;
  top: 5px;
  
}
</style>
