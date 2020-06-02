<template>
	<div>		
		<div @click="goback">返回</div>
		<div v-if="movie.img">
			<div>
				<img :src="movie.img.replace('/w.h/','/500.500/')" />
			</div>
			<div>
				{{movie.nm}}
			</div>
			<div>
				{{movie.cat}}
			</div>
			<div>
				{{movie.pubDesc}}
			</div>
			<div>
				{{movie.dra}}
			</div>
		</div>	
	</div>
</template>

<script>
	import axios from 'axios'
	export default{
		data(){
			return {
				movie:{}
			}
		
		},
		created()
		{
			let id = this.$route.params.id;
			this.getDetail(id);
		},
		watch:
		{
			$route(oldv,newv)
			{
				let id = this.$route.params.id;
				if(id)
				{
					this.getDetail(id);
				}
			}
		},
		methods:{
			goback()
			{
				this.movie = {};
				this.$router.go(-1);
			},
			getDetail(id)
			{
				axios.get(`/api/ajax/detailmovie?movieId=${id}`)
				.then(res=>{
					console.log(res);
					
					this.movie = res.data.detailMovie;
				})
			}
		}
	}
</script>

<style>
</style>
