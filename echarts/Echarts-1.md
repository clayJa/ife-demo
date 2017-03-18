# Echarts入门之柱状折线混合图
### step 1：
创建容器
```html
<div id= "main"></div>
```
### step 2：
引入Echarts.js
```javascript
<script src="http://echarts.baidu.com/vendors/jquery/jquery.min.js"></script>
```
### step 3:
ajax获取未来24小时温度数据
API：[天气查询](https://market.aliyun.com/products/57096001/cmapi011242.html)
### step 4：
Echarts参数option配置
```javascript
 var option = {
 //标题
    title: {
        text: data.result.city + '未来24小时温度变化',
        left: 180
    },
    tooltip: {
    },
 //图例
    legend: {
        data:['温度柱形图','温度折线图'],
        right: 150
    },
//横坐标
    xAxis: {
    	type: 'category',
        data: time,
    },
//纵坐标
    yAxis: {
    	type: 'value',
        name: '温度/℃',
        min: 0,
        max: max,
        interval: (max - min)/5
    },
//数据表现形式及数据
    series: [{
        name: '温度柱形图',
        type: 'bar',
        barWidth: 10,
        data: temp
    },
    {
        name: '温度折线图',
        type: 'line',
        data: temp
    }
    ]
};
```
### step 5
生成
```javascript
myChart.setOption(option);
```
