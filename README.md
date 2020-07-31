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

## 安装v-org-chart包
npm i v-org-chart

## 参数
orgChartData

例:
```
<v-org-chart :orgChartData="res"/>

import vOrgChart from 'v-org-chart'

 
data(){
	return {
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