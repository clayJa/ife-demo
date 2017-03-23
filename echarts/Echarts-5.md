# Echarts入门之动态数据
### 数据动态更新
通过不断更新option，定时获取数据，setOption 填入数据
定时：setInterval()
清除定时：window.clearInterval(id);参数为 setInterval() 返回的 ID 值。
数据处理：arrayObject.push(newelement)  arrayObject.shift(newelement)