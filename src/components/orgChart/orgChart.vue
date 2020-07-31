<template>
  <div class="struWrap">
		<div class="childWrap"  v-for="(item,index) in orgStruData" :key=index >
			<div class="orgLevel">
				<i>{{item[showField]}}</i>
			</div>
			<orgChart v-if="item.child&&item.child.length!=0" :orgStruData=item.child :direction="direction" :showField="showField" /> 
		</div>
  </div>
</template>

<script>
	export default {
		name: 'orgChart',
		props:[
			'orgStruData',
			'direction',
			'showField'
		]
	}
</script>
<style scoped>
	.upDown .childWrap{float: left;margin: 20px auto;width: max-content;}
	.upDown .orgLevel{line-height: 26px;margin:0 10px}
	.upDown .orgLevel i{
		border: 1px solid #000;
		padding: 3px 8px;
		font-style: normal;
		border-radius: 5px;
	}
	.leftRight .childWrap{margin-left:10px}
	.leftRight .orgLevel{vertical-align: middle;
    display: inline-block;margin:10px 0 0 6px;}
	.leftRight .orgLevel i{border: 1px solid #000;
		padding: 3px 8px;
		font-style: normal;
		border-radius: 5px;}
	.leftRight .struWrap{vertical-align: middle;
    display: inline-block;}

</style>
