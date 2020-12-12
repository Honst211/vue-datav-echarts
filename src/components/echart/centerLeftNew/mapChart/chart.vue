<template>
  <div>
    <Echart
      :options="options"
      id="mapChart"
      height="5.6rem"
      width="100%"
    ></Echart>
  </div>
</template>

<script>
import Echart from '@/common/echart'
export default {
  data () {
    return {
      options: {},
    };
  },
  components: {
    Echart,
  },
  props: {
    cdata: {
      type: Object,
      default: () => ({})
    },
  },
  watch: {
    cdata: {
      handler (newData) {
        this.options = {
          // backgroundColor: '#000',
          // 悬浮提示
          tooltip: {
              trigger: "item",
              backgroundColor: "#1540a1",
              borderColor: "#FFFFCC",
              showDelay: 0,
              hideDelay: 0,
            // enterable: true,
              transitionDuration: 0,
            // extraCssText: "z-index:100",formatter
              formatter: function (params, ticket, callback) {
                  // 根据业务自己拓展要显示的内容
                  var res = "";
                  var name = params.name;
                  var value = params.value[params.seriesIndex + 1];
                  res = "<span style='color:#fff;'>" + name.toString().split(' ')[0]
                      + "</span><br/>服务器：" + name.toString().split(' ')[1];
                  return res;
              }
          },
          visualMap: {
              // 图例值控制
              min: 0,
              max: 10000,
              text:['High','Low'],
              show: false,
              calculable: true,
              // color: ["#0bc7f3"],
              color: ['orangered','yellow','lightskyblue']
          },
          geo: {
              map: "world",
              label: {
                  emphasis: {
                      show: false
                  }
              },
              roam: true, // 是否允许缩放
              layoutCenter: ["50%", "50%"], // 地图位置
              layoutSize: "180%",
              itemStyle: {
                  normal: {
                      color: ["#04284e"], // 地图背景色
                      // color: ['orangered','yellow','lightskyblue']
                      borderColor: "#5bc1c9", // 省市边界线
                      areaColor:'#09295b'//默认区域颜色
                  },
                  emphasis: {
                      color: "rgba(37, 43, 61, .5)", // 悬浮背景
                      areaColor:'#3066ba'//默认区域颜色
                  }
              }
          },
          series: newData.series
          };
        },
        immediate: true,
        deep: true
    },
  },
}
</script>

<style lang="scss" scoped>
</style>