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
			<div :class="{limitedheight:flag}" style="text-align: left;overflow: hidden;">
				{{movie.dra}}
			</div>
			<div>
				<img :src="flag?downIcon:upIcon" @click="flag=!flag"/>
			</div>
		</div>	
	</div>
</template>

<script>
	import axios from 'axios'
	import downIcon from '../assets/down.png'
	import upIcon from '../assets/up.png'
	export default{
		data(){
			return {
				flag:true,/**height: 50px**/
				movie:{},
				downIcon,
				upIcon
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
			},
			/* toggle()
			{
				if(this.flag)
				{
					this.iconpath = upIcon;
				}
				else
				{
					this.iconpath = downIcon;
				}
				
				this.flag = !this.flag;
			} */
		}
	}
</script>

<style>
	.limitedheight{
		height: 50px;
	}
</style>
