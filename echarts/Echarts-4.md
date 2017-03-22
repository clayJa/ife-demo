# Echarts入门之可视化前的数据预处理
### step 1
使用 Node.js 
通过[node-csvtojson插件](https://github.com/Keyang/node-csvtojson)将获取的 csv 格式的数据转换成json格式
安装：
```javascript
npm i --save csvtojson
```
转化：
```javascript
csvtojson source.csv > data.json
```
注意：
#### 在转换前，在csv文件的头部插入一行，可指定json文件key名。在这里为：Date, Ticker, Open, High, Low, Close, Volume。否则转换中插件会自动把第一行数据最为json中的key名进行转换。
### step 2
数据处理
```javascript
var dataSolve = function(data){
	var date = [],value = [],volume = [],temp = [],i,len;
	len = data.length;
	for(i = 0;i < len;i++ ){
		if(data[i]["Ticker"] === "A"){
			date.push(data[i]["Date"].replace(/(\d{4})(\d{2})(\d{2})/,"$1-$2-$3"));
			temp = [];
			temp.push(parseFloat(data[i]["Open"]));
			temp.push(parseFloat(data[i]["Close"]));
			temp.push(parseFloat(data[i]["Low"]));
			temp.push(parseFloat(data[i]["High"]));
			value.push(temp);
			volume.push(parseInt(data[i]["Volume"]));
		}
		else{
			break;
		}
	}
	return{
		date: date,
		value: value,
		volume: volume
	};
}
```
注意：
#### K线图数据顺序：[open, close, lowest, highest] （即：[开盘值, 收盘值, 最低值, 最高值]）
### step 3 dataZoom 与 多个grid
