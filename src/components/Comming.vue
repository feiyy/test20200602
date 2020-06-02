<template>
	<div>
		<div>
			近期最受期待
			<div class="flexbox">
				<div class="flexitem" v-for="item in expectedList">
					<img :src="item.img.replace('/w.h/','/100.100/')" />
					<div>{{item.nm}}</div>
					<div>{{item.comingTitle}}</div>
				</div>
			</div>
		</div>
		
	</div>
</template>

<script>
	import axios from 'axios'
	export default{
		data(){			
			return {
				expectedList:[]
			}			
		},
		created()
		{
			axios.get('/api/ajax/mostExpected?ci=57&limit=10&offset=0&token=')
			.then(res=>{
				console.log(res);
				this.expectedList = res.data.coming;
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
		border:1px solid red;
		flex-shrink: 0;
	}
</style>
