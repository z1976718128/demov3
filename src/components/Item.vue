<template>
	<div>
		<van-cell >
		  <template slot="title">
				<van-row  v-for="(item,index) in dataArr" :key="index" class="bor_top" @click="bpIndex(item.id)">
				  <van-col span="24">
					  <p class="bt">
						  <van-tag v-if="item.stage_name" color="#FEF3DC">{{item.stage_name}}</van-tag>
						  <span class="title">{{item.title}}</span>
					   </p>
					  <p class="nth_p">
						  <span class="capital_name">{{item.capital_name}}</span>
						  <van-tag  v-for="(field,index) in item.field_name" :key="index" class="tang2" color="#FFF3EB">{{field}}</van-tag>
						  <van-tag v-if="item.status == 0" color="#1767E7">审查中</van-tag>
						  <van-tag v-if="item.status == 1" color="#9FB534">洽谈中</van-tag>
						  <van-tag v-if="item.status == 2" color="#9FB534">对接中</van-tag>
						  <van-tag v-if="item.status == 3" color="#494949">融资失败</van-tag>
						  <van-tag v-if="item.status == 4" color="#494949">融资失败</van-tag>
					  </p>
					  <p class="footer_p">
						<span>{{item.add_time}}</span>  
						<span>浏览量：{{item.volume_num}}</span>
					  </p>
				  </van-col>
				</van-row>
		  </template>
		</van-cell>
	</div>
</template>

<script>
export default{
	props:["dataArr"],
	methods:{
		bpIndex(id){
			console.log(id)
			this.$router.push({path:"/bp",query:{id:id}})
		}
	}
}	
</script>

<style scoped lang="less">
.title{
	margin-left: 7px;
}
.bt .van-tag{
	color: #DEA32C;
}	
.tang2{
	color: #FF9C82 !important;
}
.capital_name{
	font-size:25px;
	font-weight:bold;
	color:rgba(243,140,55,1);
}
.nth_p{
	display: flex;
	justify-content: space-between;
}
.footer_p{
	font-size:12px;
	font-weight:400;
	color:rgba(181,181,181,1);
	display: flex;
	justify-content: space-between;
}
.bor_top{
	border-top:1px solid rgba(241,241,241,1) ;
}
@media (min-width:750px) {
	.title{
		margin-left: 7px;
	}
	.van-tag{
		color: #DEA32C;
	}	
	.tang2{
		color: #FF9C82 !important;
	}
	.capital_name{
		font-size:25px;
		font-weight:bold;
		color:rgba(243,140,55,1);
	}
	.nth_p{
		display: flex;
		justify-content: space-between;
	}
	.footer_p{
		font-size:12px;
		font-weight:400;
		color:rgba(181,181,181,1);
		display: flex;
		justify-content: space-between;
	}
	.bor_top{
		border-top:1px solid rgba(241,241,241,1) ;
	}
}
</style>
