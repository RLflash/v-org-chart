<template>
  <div class="struWrap">
		<div class="childWrap"  v-for="(item,index) in orgStruData" :key=index >
			<div class="orgLevel">
				<i>{{item.level}}</i>
			</div>
			<orgChart v-if="item.child&&item.child.length!=0" :orgStruData=item.child /> 
		</div>
  </div>
</template>

<script>
	export default {
		name: 'orgChart',
		props:['orgStruData'],
	}
</script>
<style scoped>
	.childWrap{float: left;margin: 20px auto;width: max-content;}
	.orgLevel{line-height: 26px;margin:0 10px}
	.orgLevel i{
    border: 1px solid #000;
    padding: 3px 8px;
    font-style: normal;
    border-radius: 5px;
}
</style>
