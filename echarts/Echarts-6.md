# Echarts入门之绘制人物关系图
### step 1
从 [http://www-personal.umich.edu/~mejn/netdata/](http://www-personal.umich.edu/~mejn/netdata/) 选择一份关系数据下载
### step 2
用 [gephi](https://gephi.org/) 对数据进行处理，布局，分类后导出成 gexf 格式。
[快速入门](https://gephi.org/users/quick-start/)
[详细教程](https://gephi.org/users/tutorial-visualization/)
[布局](https://gephi.org/users/tutorial-layouts/)
### step 3
通过echarts.dataTool解析gexf数据；
echarts.js并没有内置dataTool，需要自己[下载](https://github.com/ecomfe/echarts/blob/master/dist/extension/dataTool.min.js)并引入
#### echarts.dataTool
```javascript
Object {version: "1.0.0", gexf: Object}
```
#### echarts.dataTool.gexf
```javascript
Object {parse: t(e), __proto__:Object} 
```
#### echarts.dataTool.gexf.parse(xml)返回值
xml为需要解析的gexf文件
```javascript
Object {
	nodes: Array[34],
	links: Array[78],
	__proto__: Object
}
```
##### nodes包含gexf图中的节点数据
```javascript
{
	attributes:{
	betweenesscentrality:0,
	closnesscentrality:0,
	eccentricity:0,
	harmonicclosnesscentrality:0,
	modularity_class:0,  //模块值
	__proto__:Object
	},
	category:0,//类别
	id:"1.0",
	//节点样式
	itemStyle:{
		normal:{
			color:"rgb(104,173,54)",
			__proto__:Object
		},
	__proto__:Object
	},
	name: "1.0",
	symbolSize: 47.5,  //关系图节点标记的大小
	x:33.86796,
	y:388.1594
}
```
所对应的xml文档
```xml
<node id="1.0" label="1.0">
	<attvalues>
	  <attvalue for="eccentricity" value="0.0"></attvalue>
	  <attvalue for="closnesscentrality" value="0.0"></attvalue>
	  <attvalue for="harmonicclosnesscentrality" value="0.0"></attvalue>
	  <attvalue for="betweenesscentrality" value="0.0"></attvalue>
	  <attvalue for="modularity_class" value="0"></attvalue>
	</attvalues>
	<viz:size value="47.5"></viz:size>
	<viz:position x="33.86796" y="388.1594"></viz:position>
	<viz:color r="104" g="173" b="54"></viz:color>
</node>
```
##### links包含gexf图中的边数据
```javascript
{
	id:"1",
	lineStyle:{
		normal:{
			color:"rgb(0,109,44)",
			__proto__:Object		
			},
		__proto__:Object
	},
	name: null,
	source :"3.0",
	target: "1.0"
}
```
对应的xml文档
```xml
<edge id="0" source="2.0" target="1.0">
	<viz:color r="0" g="109" b="44"></viz:color>
</edge>
```