<template>
  <div>
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue'
export default {
  data () {
    return {
      cdata: {
        series : []
      }
    };
  },
  components: {
    Chart,
  },
  mounted () {
    this.getSeries()
  },
  methods: {
    getSeries(){
        var geoCoordMap = {
          北京: [116.28, 39.54],
        // 杭州: [120.10, 30.15],
        // 南宁: [108.479, 23.1152],
        // 广州: [113.5107, 23.2196],
          重庆: [107.7539, 30.1904],
          上海: [121.4648, 31.2891],
          尼日利亚: [-4.388361, 11.186148],
          洛杉矶: [-118.24311, 34.052713],
          香港: [114.195466, 22.282751],
          芝加哥: [-87.801833, 41.870975],
          加纳库马西: [-4.62829, 7.72415],
          曼彻斯特: [-1.657222, 51.886863],
          汉堡: [10.01959, 54.38474],
          阿拉木图: [45.326912, 41.101891],
          伊尔库茨克: [89.116876, 67.757906],
          巴西: [-48.678945, -10.493623],
          埃及: [31.815593, 31.418032],
          巴塞罗纳: [2.175129, 41.385064],
          柬埔寨: [104.88659, 11.545469],
          米兰: [9.189948, 45.46623],
          蒙得维的亚: [-56.162231, -34.901113],
          莫桑比克: [32.608571, -25.893473],
          阿尔及尔: [3.054275, 36.753027],
          阿联酋迪拜: [55.269441, 25.204514],
          布达佩斯: [17.108519, 48.179162],
          悉尼: [150.993137, -33.675509],
          加州: [-121.910642, 41.38028],
          墨尔本: [144.999416, -37.781726],
          墨西哥: [-99.094092, 19.365711],
          温哥华: [-123.023921, 49.311753]
      };
      var BJData = [[{
          name: "北京",
          value: 12580
      }],[{
          name: "重庆",
          value: 10000000
      }],[{
          name: "上海",
          value: 9100
      }], [{
          name: "尼日利亚",
          value: 9100
      }], [{
          name: "洛杉矶",
          value: 2370
      }], [{
          name: "香港",
          value: 3130
      }], [{
          name: "芝加哥",
          value: 2350
      }], [{
          name: "加纳库马西",
          value: 5120
      }], [{
          name: "曼彻斯特",
          value: 3110
      }], [{
          name: "汉堡",
          value: 6280
      }], [{
          name: "阿拉木图",
          value: 7255
      }], [{
          name: "伊尔库茨克",
          value: 8125
      }], [{
          name: "巴西",
          value: 3590
      }], [{
          name: "埃及",
          value: 3590
      }], [{
          name: "巴塞罗纳",
          value: 3590
      }], [{
          name: "柬埔寨",
          value: 3590
      }], [{
          name: "米兰",
          value: 3590
      }], [{
          name: "蒙得维的亚",
          value: 3590
      }], [{
          name: "莫桑比克",
          value: 3590
      }], [{
          name: "阿尔及尔",
          value: 31590
      }], [{
          name: "阿联酋迪拜",
          value: 13590
      }], [{
          name: "布达佩斯",
          value: 23590
      }], [{
          name: "悉尼",
          value: 3590
      }], [{
          name: "加州",
          value: 3590
      }], [{
          name: "墨尔本",
          value: 3590
      }], [{
          name: "墨西哥",
          value: 3590
      }], [{
          name: "温哥华",
          value: 3590
      }]];

      var series = [];
      [[, BJData]].forEach(function (item, i) {
          series.push({
              type: "effectScatter",
              coordinateSystem: "geo",
              zlevel: 2,
              rippleEffect: {
                  //涟漪特效
                  period: 4, //动画时间，值越小速度越快
                  brushType: "stroke", //波纹绘制方式 stroke, fill
                  scale: 4
                  //波纹圆环最大限制，值越大波纹越大
              },
              label: {
                  normal: {
                      show: true,
                      position: "right", //显示位置
                      offset: [5, 0], //偏移设置
                      formatter: "{b}" //圆环显示文字
                  },
                  emphasis: {
                      show: true
                  }
              },
              symbol: "circle",
              symbolSize: function (val) {
                  var  level = 0 ;
                  var state= Math.floor(val[2]/5000) ;
                  switch (state)
                  {
                      case 0: level=0; break;
                      case 1: level=1; break;
                      case 2: level=2; break;
                      case 3: level=3; break;
                      case 4: level=4; break;
                      case 5: level=5; break;
                      case 6: level=6; break;
                      case 7: level=7; break;
                      case 8: level=8; break;
                      case 9: level=9; break;
                      default: level=10;
                  }
                  return 5 + level; //圆环大小
              },
              data: item[1].map(function (dataItem) {
                  return {
                      name: dataItem[0].name/*+"\n"+dataItem[0].value*/,
                      value: geoCoordMap[dataItem[0].name]
                          .concat([dataItem[0].value])
                  };
              })
          });
      });
      this.cdata.series = series
    }
  }
};
</script>

<style lang="scss" scoped>
</style>