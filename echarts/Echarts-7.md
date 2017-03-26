# Echarts入门之空气质量可视化
#### 获取China地图，作为geo数据
#### 获取city坐标数据与aqi数据，处理为适合散点图(scatter)数据
#### 根据柱状图和折线图需要处理数据
#### 为散点图添加click事件，点击相应城市查看该城市所有事件aqi数据
#### 动态展示每天各地aqi数据
#### 数据处理函数
```javascript
        /*********************************/

        //对数据按天进行分割
        /* @param
        data:aqi.json返回数据
        aqi.json格式
            [{
                "city": "湛江",
                "aqi": "57",
                "date": "2000/6/5"
            }]
        返回值dailyAqi格式：
        {
            {
                name: "湛江",
                value: 57
            }
        }
        */
        var dataSplit = function(data){
            if(data[0] !== undefined){
                var dailyAqi = {},len;
                var dateIndex = data[0].date;
                len = data.length;
                for(var i = 0;i < len;i++){
                    if (data[i] != undefined) {
                        dateIndex = data[i]["date"];
                        if(!(dailyAqi[dateIndex] instanceof Array)){
                            dailyAqi[dateIndex] = [];
                        }
                        dailyAqi[dateIndex].push({
                            name: data[i]["city"],
                            value: parseInt(data[i]["aqi"])
                        });
                    }
                    
                    
                }
                return dailyAqi;

            }
        }
        //对数据按城市进行分割
       /* @param
        data:aqi.json返回数据
        aqi.json格式
            [{
                "city": "湛江",
                "aqi": "57",
                "date": "2000/6/5"
            }]
        返回值cityAqi格式：
        {[
            "2000/6/5",
            57
        ]}
        */
        var dataSplitByCity = function(data){
            if(data[0] !== undefined){
                var cityAqi = {},len;
                var cityIndex = data[0].city;
                len = data.length;
                for(var i = 0;i < len;i++){
                    if (data[i] != undefined) {
                        cityIndex = data[i]["city"];
                        if(!(cityAqi[cityIndex] instanceof Array)){
                            cityAqi[cityIndex] = [];
                        }
                        cityAqi[cityIndex].push([
                            data[i]["date"],
                            parseInt(data[i]["aqi"])
                        ]);
                    }
                    
                    
                }
                return cityAqi;

            }
        }
        //将数据处理为散点图接受的数据
        /* @param
        city:经过处理的city.json数据
        格式
            {
                "湛江": [110.40075302124023,21.19657588798597]
            }
        data:经过dataSplit()处理返回的某天数据
        格式：
        {
            {
                name: "湛江",
                value: 57
            }
        }
        返回值result格式
        [
            {
                name: "湛江",
                value: [110.40075302124023,21.19657588798597,57]
            }
        ]

        */
        var dataParse = function(city,data){
            var result = [],cityPoint,len,index;
            len = data.length;
            for(index = 0; index < len; index++ ){
                cityPoint = city[data[index]["name"]];
                result.push({
                    name: data[index]["name"],
                    value: cityPoint.concat(data[index]["value"])
                })
            }
            return result;
        }


```