<template>
	  <div class="swiper-container bannerId">
	  	<div class="swiper-wrapper" >
	  		<div class="swiper-slide" v-for="(banner,index) in bannerData" :key="index" @click="gotoBanner(banner)">
	  			<img class="swi_img"  :src="banner.img" alt="">
	  			<!-- <p class="swp_p">{{banner.title}}</p> -->
	  		</div>
	  	</div>
	  	<div class="swiper-pagination"></div>
	  </div>
</template>

<script>
	import {newInc} from '@/api/api.js'
export default {
	props:["bannerData"],
	methods:{
		gotoBanner(banner){
			if (banner.href !="") {
				window.location.href =banner.href
				newInc({
					id:banner.id
				}).then(res=>{
					console.log(res)
				})
			}else{
				this.$router.push({
				  path: "/findDetails",
				  query: {
				    id: banner.id
				  }
				})
			}
		}
		
	}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.bannerId{
	// width: 90%;
	height: 146px;
	margin-top:12.5px;
	img{
		width: 100%;
		height: 100%;
		border-radius: 12px;
	}
}	
@media (min-width:750px) {
	.bannerId{
		// width: 90%;
		height: 146px;
		margin-top:12.5px;
		img{
			width: 100%;
			height: 100%;
			border-radius: 12px;
		}
	}	
}
</style>
