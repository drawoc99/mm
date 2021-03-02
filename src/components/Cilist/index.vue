<template>
    <div class="cinema_body">
				<ul>
					
					<li v-for="item in CinemasList.slice(1)" :key="item.id">
						<div>
							<span>{{item.name}}</span>
							<span class="q"><span class="price"></span>38 元起</span>
						</div>
						<div  class="address" >
							<span>金牛区北二环路10号</span>
							<span>500m</span>
						</div>
						<div class="card">
                			<div>小吃</div>
                			<div>折扣卡</div>
       					</div>
					</li>
				</ul>
		</div>
</template>


<script>
export default {
    name:'CiList',
	data(){
		return{
			CinemasList:[],
			
		}
	},
	mounted(){
		this.axios.get('ajax/filterCinemas?ci=59&optimus_uuid=78519F10773111EB88D4C1535D48DC33F89ED6A423FF4486B695F95EA050054E&optimus_risk_level=71&optimus_code=10').then((res)=>{
				this.CinemasList=res.data.brand.subItems;
				
		})
	}
}
</script>

<style scoped>
#content .cinema_body{ flex:1; overflow:auto;}
.cinema_body ul{ padding:20px;}
.cinema_body li{  border-bottom:1px solid #e6e6e6; margin-bottom: 20px;}
.cinema_body div{ margin-bottom: 10px;}
.cinema_body .q{ font-size: 11px; color:#f03d37;}
.cinema_body .price{ font-size: 18px;}
.cinema_body .address{ font-size: 13px; color:#666;}
.cinema_body .address span:nth-of-type(2){ float:right; }
.cinema_body .card{ display: flex;}
.cinema_body .card div{ padding: 0 3px; height: 15px; line-height: 15px; border-radius: 2px; color: #f90; border: 1px solid #f90; font-size: 13px; margin-right: 5px;}
.cinema_body .card div.or{ color: #f90; border: 1px solid #f90;}
.cinema_body .card div.bl{ color: #589daf; border: 1px solid #589daf;}

</style>