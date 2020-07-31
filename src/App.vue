<template>
  <div id="app">
			<org-chart :orgChartData="res" :direction="direction" :showField="showField"/>
  </div>
</template>

<script>
import orgChart from './components/orgChart'
export default {
  name: 'App',
  components: {
    orgChart
  },
	data(){
		return {
			direction:'upDown',
		//	showField:'level',
			res:[{level:'皇帝',
					child:[{
							level:'将军',
							child:[{
								level:'百夫长1',
								child:[{
									level:'伍长11',
									child:[{
										level:'武卒111',
										child:[]
									},{
										level:'武卒112',
										child:[]
									}]
								},{
									level:'伍长12',
									child:[{
										level:'武卒121',
										child:[]
									},{
										level:'武卒122',
										child:[]
									},{
										level:'武卒123',
										child:[]
									},{
										level:'武卒124',
										child:[]
									}]
								}]
							},{
									level:'百夫长2',
									child:[{
										level:'伍长22',
										child:[{
											level:'武卒221',
											child:[]
										}]
									}]
								}]
						}]
				}]
		}
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
