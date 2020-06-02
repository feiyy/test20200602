<template>
	
	<!-- <router-link :to="'/detail/'+item.id"> -->
		<div class="item" @click="$router.push('/detail/'+item.id)">
			<div class="left">
				<img :src="item.img.replace('/w.h/','/100.100/')" />
			</div>
			<div class="middle">
				<div class="title">{{item.nm}}</div>
				<div class="info">
					<div v-if="item.globalReleased">
						观众评<span>{{item.sc}}</span>
					</div>
					<div v-else>
						<span>{{item.wish}}</span>想看
					</div>			 
				</div>
				<div class="info">{{item.star}}</div>
				<div class="info">{{item.comingTitle}}</div>
			</div>
			<div class="right">
				<button v-if="item.globalReleased" type="button">购票</button>
				<button v-else type="button">预售</button>
			</div>
		</div>
	<!-- </router-link> -->
	
</template>

<script>
	export default{
		props:['item']
	}
</script>

<style lang="less">
	.item{
		display: flex;
	}
	.left{
		width:100px;
	}
	.middle{
		width:calc(100% - 160px); /**get all the left room**/
		text-align: left;	
		
		.info{
			overflow: hidden; 
			white-space: nowrap; 
			text-overflow: ellipsis;
		}
	}
	
	
	.right{
		width:60px;
		display: flex;
		align-items: center;
	}
</style>
