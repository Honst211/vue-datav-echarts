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
        category: [
          "2015",
          "2016",
          "2017",
          "2018",
          "2019",
          "2020"
        ],
        proData: [
          183,
          1631,
          1284,
          1341,
          178,
          407
        ],
        deskData: [
          123,
          2345,
          1234,
          4321,
          332,
          671
        ],
        comData: [
          321,
          3245,
          6321,
          2356,
          666,
          841
        ]
      }
    };
  },
  components: {
    Chart,
  },
  mounted () {
    // this.setData();
  },
  methods: {
    // 根据自己的业务情况修改
    setData () {
      for (let i = 0; i < this.cdata.barData.length -1; i++) {
        let rate = this.cdata.barData[i] / this.cdata.lineData[i];
        this.cdata.rateData.push(rate.toFixed(2));
      }
    },
  }
};
</script>

<style lang="scss" scoped>
</style>