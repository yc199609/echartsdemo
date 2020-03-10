<template>
    <div id="main" style="width: 600px;height:400px;"></div>
</template>

<script>
import echarts from 'echarts'

export default {
    name: 'App',
    mounted(){
        var myChart = echarts.init(document.getElementById('main'));

            // 指定图表的配置项和数据
            var option = {
                title: {
                    text: 'ECharts 入门示例'
                },
                tooltip: {},
                xAxis: {},
                yAxis: {},
                series: [{
                    type: 'line',
                    data:[ [20, 120], [50, 200], [40, 50]]
                },
                {
                    type: "line",
                    showSymbol: false,
                    clip: true,
                    data: this.generateData()
                }
                ]
            };

            // 使用刚指定的配置项和数据显示图表。
            myChart.setOption(option);
    },
    methods:{
        generateData(){
            let data = [];
            for (let i = 0; i < 360; i ++  ){
                data.push(this.fn(i));
            }
            return data
        },
        fn(rot){
            var x0 = 20 // 圆心x
            var y0 = 50 // 圆心y
            var a = 20 // 长轴
            var b = 50 // 短轴
            var y = b * Math.sin(Math.PI * rot / 180) + y0
            var x = a * Math.cos(Math.PI * rot / 180) + x0
            return [ x, y];
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
