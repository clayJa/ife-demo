# Echarts入门之绘制地图
### step 1
从 [naturalearth](http://www.naturalearthdata.com/) 下载原始的世界地图数据
并通过[mapshaper](http://mapshaper.org/)转成 GeoJSON 格式。
### step 2
通过ajax获取json数据
```javascript
$.get("../echarts/map/countries.json",function(earth){
    //数据处理
    });
```
### step 3
了解[GeoJSON](http://geojson.org/)数据格式，获取地名，进而生成series配置项所需data数据
```javascript
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [125.6, 10.1]
  },
  "properties": {
    "name": "Dinagat Islands"
  }
}
```
### step 4
注册地图名字和数据
```javascript
echarts.registerMap('countries', earth);
```
### step 5
通过visualMap 为series-map映射颜色
```javascript
visualMap: {
    left: 60,
    //min max 对应value的值
    top: 250,
    min: 1,
    max: 172,
    inRange: {
    	color: ["#339933","#99CC33","#33CC99","#CCCC00","#CCCC44","#CC6600","#FF9900","#FFFF00","#FF6666","#FF9966"]
    },
    text:['High','Low'],           // 文本，默认为数值文本
    calculable: true
}
```