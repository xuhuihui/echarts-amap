# ECharts Extension AMap

An echarts extension to support AMap(http://lbs.amap.com/), Ported from the offical echarts `extension-bmap`

> https://github.com/ecomfe/echarts/tree/master/extension/bmap

## Install

```bash
npm install -S echarts-amap
```

## Get Started

**Using Script Tag**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>ECharts AMap Test</title>
    <style>
    html,body,#map {
      margin: 0;
      padding: 0;
      height: 100%;
    }
    </style>
  </head>
  <body>
    <div id="map"></div>

    <!-- external dependencies -->
    <script src="http://webapi.amap.com/maps?v=1.3&key=YOUR_AMAP_API_KEY&plugin=AMap.CustomLayer"></script>
    <script src="http://cdn.bootcss.com/echarts/3.4.0/echarts.min.js"></script>

    <!-- import the extension -->
    <script src="node_modules/echarts-amap/dist/echarts-amap.min.js"></script>

    <script type="text/javascript">
      var echart = echarts.init(document.getElementById('map'))
      echart.setOption({
        // use amap component
        amap: {
          center: [116.397475,39.908695],
          zoom: 5,
          mapStyle: 'blue_night'
        },
        // demo serie showing the capital BEIJING of our PRC :cn:
        series: [{
          type: 'effectScatter',
          coordinateSystem: 'amap',
          rippleEffect: {
            brushType: 'stroke'
          },
          label: {
            normal: {
              show: true,
              position: 'right',
              formatter: '{b}'
            }
          },
          symbolSize: 20,
          itemStyle: {
            normal: {
              color: '#f44336'
            }
          },
          data: [{
            name: '首都',
            value: [116.397475,39.908695]
          }]
        }]
      })
    </script>
  </body>
</html>
```

**Using Webpack**

```javascript
var echarts = require('echarts')
require('echarts-amap')

var echart = echarts.init(document.getElementById('map'))
echart.setOption({
  ... // see the example above
})
```

###20180417更新日志

>支持高德地图3D地图，可以实现更多炫酷效果，部分截图如下：


![map3d-scatter](./assets/scatter.png)

![map3d-scatter](./assets/3dline.png)

**请不要参考本人示例中js的加载方式，特定环境需求，暂时没时间好好整理，等有时间会整理几种情况下的demo**
