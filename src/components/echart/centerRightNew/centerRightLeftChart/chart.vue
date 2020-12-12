<template>
  <div>
    <Echart
      :options="options"
      id="centerRightLeftChart"
      height="2.6rem"
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
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'cross',
                        crossStyle: {
                            color: '#999'
                        }
                    }
                },
                legend: {
                    data: ['全球数1', '全球数2', '全球数3']
                },
                grid: {
                  left: "6%",
                  right: "4%",
                  bottom: "10%",
                  containLabel: true,
                },
                xAxis: [
                    {
                        type: 'category',
                        data: newData.category,
                        axisPointer: {
                            type: 'shadow'
                        }
                    }
                ],
                yAxis: [
                    {
                        type: 'value',
                        name: '总数(台)'
                    }
                ],
                series: [
                    {
                        name: '全球数1',
                        type: 'bar',
                        data: newData.proData
                    },
                    {
                        name: '全球数2',
                        type: 'bar',
                        data: newData.deskData
                    },
                    ,
                    {
                        name: '全球数3',
                        type: 'bar',
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