<template>
	<div>
		<div>
			近期最受期待
			<div class="flexbox">
				<div class="flexitem" v-for="item in expectedList">
					<img :src="item.img.replace('/w.h/','/100.100/')" />
					<div style="font-size: 14px;white-space: nowrap;overflow: hidden;text-overflow: ellipsis;">{{item.nm}}</div>
					<div>{{item.comingTitle}}</div>
				</div>
			</div>
		</div>
		<div style="margin-top:20px">
		    <MovieItem v-for="item in movieList" :item="item" :key="item.id"></MovieItem>
		</div>
		
	</div>
</template>

<script>
	import MovieItem from './MovieItem.vue'
	import axios from 'axios'
	export default{
		data(){			
			return {
				expectedList:[],
				movieList:[]
			}			
		},
		components:{
			MovieItem
		},
		created()
		{
			//to get expected
			axios.get('/api/ajax/mostExpected?ci=57&limit=10&offset=0&token=')
			.then(res=>{
				console.log(res);
				this.expectedList = res.data.coming;
			})
			
			//to get comming
			axios.get('/api/ajax/comingList?ci=57&token=&limit=10')
			.then(res=>{
				console.log(res);
				
				this.movieList = res.data.coming;
			})
		}
		
	}
</script>

<style>
	.flexbox{
		display: flex;
		overflow: auto;
		
	}
	.flexitem{
		width:25vw;
		height: 150px;
		flex-shrink: 0;
	}
</style>
