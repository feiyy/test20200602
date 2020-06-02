<template>
  <div id="app">
	  <div class="fixed">
		   <div class="title">
		   	猫眼电影
		   </div>
		   <div id="nav">
		     <router-link to="/hot">正在热映</router-link> |
		     <router-link to="/comming">即将上映</router-link>
		   </div>
	  </div>
	  <div class="content">
		 <router-view/>
	  </div>
   
  </div>
</template>

<style lang="less" scoped>	

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.fixed{
	width:100%;
	position:fixed;
	top:0px;
	left:0px;
	
	.title{
		width:100%;
		height: 50px;
		line-height: 50px;
		background-color: #e64645;
		color:white;
		font-weight: bold;
		font-size: 20px;
		
	}
	
	#nav {
	  background-color: white;
	  padding:10px;
	
	  a {
	    font-weight: bold;
	    color: #2c3e50;
	
	    &.router-link-exact-active {
	      color: #e64645;
		  text-decoration: underline;
	    }
	  }
	}
}

.content
{
	margin-top: 100px;
}

</style>
