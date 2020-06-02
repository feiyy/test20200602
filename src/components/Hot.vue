<template>
	<div>
	    <MovieItem v-for="item in movieList" :item="item" :key="item.id"></MovieItem>
	</div>
</template>

<script>
	
	import MovieItem from './MovieItem.vue'
	import axios from 'axios'
	
	export default{
		data(){
			return {
				movieList:[]
			}
		},		
		components:{
			MovieItem
		},
		created()
		{
			axios.get('/api/ajax/comingList?ci=57&token=&limit=10')
			.then(res=>{
				console.log(res);
				
				this.movieList = res.data.coming;
			})
		}
		
	}
</script>

<style>
</style>
