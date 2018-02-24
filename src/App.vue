<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
    	<div class="tab_item">
    		<router-link to="/goods">商品</router-link>
    	</div>
    	<div class="tab_item">
    		<router-link to="/ratings">评价</router-link>
    	</div>
    	<div class="tab_item">
    		<router-link to="/seller">商家</router-link>
    	</div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
	import header from "./components/header/header.vue";
	const ERR_OK = 0;
	export default{
		data() {
      return {
        seller: {
          
        }
      };
    },
		components:{
			'v-header':header
		},
		created(){
			this.$http.get('/api/seller').then((res)=>{
				res=res.body;
				if (res.errno===ERR_OK) {
					this.seller=Object.assign({}, this.seller, res.data);
				}
			})
		}
	}
</script>
<style lang="scss">
	@import "./common/sass/mixin.scss";
	.tab{
		display: flex;
		.tab_item{
			line-height: 40px;
			flex: 1;
			text-align: center;
			@include border-1px(rgba(7, 17, 27, 0.1));
			& > a{
				display: block;
        font-size: 14px;
        color: rgb(77, 85, 93);
        &.active{
        	color: rgb(240, 20, 20);
        }
			}
		}
	}
</style>