<template>
	<span class="icon" :class="classIndex"></span>
</template>

<script>
	export default{
		props:{
			type:{
				type:Number
			}
		},
		created(){
			this.classMap=['decrease','discount','special','invoice','guarantee']
		},
		computed: {
			classIndex(){
				return this.classMap[this.type];
			}
		}
	}
</script>

<style>
</style>