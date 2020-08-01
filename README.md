# v-org-chart

## 安装依赖
```
npm install
```

## 运行demo
```
npm run serve
```
![](https://img2020.cnblogs.com/blog/1064049/202007/1064049-20200731112100630-394423945.png)
![](https://img2020.cnblogs.com/blog/1064049/202008/1064049-20200801161542064-351819145.png)
## 安装v-org-chart包
npm i v-org-chart

## 参数
orgChartData
组织结构图JSON数据,类型:数组,默认为[]

direction
组织结构图结构 值为:upDown(上下结构) leftRight(左右结构); 类型:字符串,默认为upDown

showField
展示字段,根据自己需求填入值,类型:字符串,默认为""

例:
```
<org-chart :orgChartData="res" :direction="direction" :showField="showField"/>

import vOrgChart from 'v-org-chart'

 
data(){
	return {
		direction:'upDown',
		showField:'level',
		res:[{
			level:'皇帝',
			child:[{
				level:'将军',
				child:[{
					level:'百夫长1',
					child:[]
				}]
			}]
		}]
	}
}
```