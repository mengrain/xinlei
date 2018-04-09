<template>
	<div id="app">
		<div class="line"></div>
		<el-menu :default-active="jgr" class="el-menu-demo" mode="horizontal" @select="handleSelect" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
        
      <el-menu-item index="1"><router-link to="/">首页</router-link></el-menu-item>
			<el-menu-item index="2"><router-link to="/1">1705A</router-link></el-menu-item>
			<el-menu-item index="3"><router-link to="/2">待重修</router-link></el-menu-item>
			<el-menu-item index="4"><router-link to="/3">已经重修</router-link></el-menu-item>

		</el-menu>
		<router-view/>
	</div>
</template>

<script>
	export default {
    components:{
      
    },
    created(){
      if(this.$route.params.id==null){
        this.jgr="1"
      }else{
        this.jgr=parseInt(this.$route.params.id)+1+""
      }
    },
    watch:{
      '$route'(){
        if(this.$route.params.id==null){
        this.jgr="1"
      }else{
        this.jgr=parseInt(this.$route.params.id)+1+""
      }
      }
    },
    data() {
      return {
        jgr: ""
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style>
	* {
		margin: 0;
		padding: 0;
	}
	
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: #2c3e50;
	}
	
	a {
		text-decoration: none;
	}
</style>