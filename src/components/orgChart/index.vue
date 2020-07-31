<template>
	<div id="orgChartWrap">
		<canvas id="lineCanvas"></canvas>
		<orgChart id="orgChart" :orgStruData=orgChartData />
		</div>
</template>

<script>
import orgChart from './orgChart.vue'
export default {
	name: 'orgChartIndex',
	components: {
		orgChart
	},
	props:['orgChartData'],
	data(){
		return {
			context:null,
			lineData:[],
		}
	},
	mounted() {
		let rootNode=document.getElementById("orgChart")
		let canvas = document.getElementById("lineCanvas")
		let orgWrapW=rootNode.clientWidth
		let orgWrapH=rootNode.clientHeight

		canvas.width = orgWrapW
		canvas.height = orgWrapH
		
		this.context = canvas.getContext("2d")
		this.context.lineWidth = 1
		this.context.strokeStyle = "black"
		for(let n=0;n<rootNode.childNodes.length;n++){
				this.getElementPosition(rootNode.childNodes[n])
		}
	
		this.lineData.forEach((item)=>{
			item.child.forEach((itemc)=>{
				this.drawLine(item.left,item.top,itemc.left,itemc.top)
			})
		})
		
	},
	methods:{
		drawLine(l,t,lc,tc){
			this.context.beginPath();
			this.context.moveTo(l, t);
			this.context.bezierCurveTo(l,t+10,lc,t,lc,tc);
			this.context.stroke();
		},
		getLinePositon(nodeEle){
			let childNode=nodeEle.childNodes;
			let elePosition;
			for(let n=0;n<childNode.length;n++){
				if(childNode[n].className=="orgLevel"){
					elePosition={top:childNode[n].offsetTop+childNode[n].clientHeight,left:childNode[n].offsetLeft+childNode[n].clientWidth/2,child:[]}
				}
				if(childNode[n].className=="struWrap"){
					for(let j=0;j<childNode[n].childNodes.length;j++){
						if(childNode[n].childNodes[j].childNodes[0].className=="orgLevel"){
							elePosition.child.push({top:childNode[n].childNodes[j].childNodes[0].offsetTop,left:childNode[n].childNodes[j].childNodes[0].offsetLeft+childNode[n].childNodes[j].childNodes[0].clientWidth/2})
						}
					}
				}
			}
			return elePosition
		},
		getElementPosition(rootNode){
			this.lineData.push(this.getLinePositon(rootNode))
			let childNode=rootNode.childNodes[1].childNodes
			for(let n=0;n<childNode.length;n++){
				this.getElementPosition(childNode[n])
			}
		}
	}
}
</script>

<style scoped>
	#orgChartWrap{position:relative;text-align: initial;}
	#lineCanvas{position: relative;top:0px;left: 0;margin: 0;}
	#orgChart{position: absolute;top:0px;left: 0;margin: 0;text-align: center;}
</style>
