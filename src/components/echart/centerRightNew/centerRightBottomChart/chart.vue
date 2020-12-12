<template>
  <div>
    <Echart
      :options="options"
      id="centerRightBottomChart"
      height="3rem"
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
            color: ['#e5323e', '#006699', '#4cabce'],
            tooltip: {
                trigger: 'axis',
                axisPointer: {            // 坐标轴指示器，坐标轴触发有效
                    type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
                }
            },
            legend: {
                data: ['预估量', '测试量', '使用量']
            },
            grid: {
                left: '3%',
                right: '8%',
                bottom: '10%',
                containLabel: true
            },
            xAxis: {
                type: 'value'
            },
            yAxis: {
                type: 'category',
                data: newData.category
            },
            series: [
                {
                    name: '预估量',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.proData
                },
                {
                    name: '测试量',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.deskData
                },
                {
                    name: '使用量',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.comData
                }
            ]
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