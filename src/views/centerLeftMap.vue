<template>
  <div id="centerLeftMap">
    <mapChart/>
    <!-- 世界地图，区域化展示各个维度的数据 -->
  </div>
</template>

<script>
import mapChart from "@/components/echart/centerLeftNew/mapChart";
export default {
  data() {
      
  },
  components: {
      mapChart
  },
  mounted() {

  },
  methods: {

  }
};
</script>

<style lang="scss">
#centerLeftMap {
  padding: 0.2rem;
  height: 6.125rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
}
</style>