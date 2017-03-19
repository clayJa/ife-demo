# Echarts入门之自定义统计图表
熟悉坐标轴，标题，图例，系列颜色 等组件样式的配置
### 主副标题
```javascript
title: {
	text: "What's  my credit score?",
	textStyle: {
		fontSize: 24
	},
	top: 20,
	left: 52,
    subtext: "Puerto Rico,% decrease on a year earlier", //副标题
    subtextStyle: {
    	color: "#38393B",
    	fontSize: 21
    }
}
```
### 坐标轴
```javascript
    position: "right" , //y轴放在右侧
    inverse: true,   //是否为反向坐标轴
    //坐标对应文本
    axisLabel: {
        textStyle: {
    		color: "#38393B",
    		fontSize: 18
	    }
	}
	//刻度
	axisTick: {
		show: false
	},
	//分割线
	splitLine: {
	    lineStyle: {
	        // 使用深浅的间隔色
	        color: "#FEFEFE",
	        width: 2
	    }
	}

```
### 图表相对位置
```javascript
grid: {
	top: 130
}
```
