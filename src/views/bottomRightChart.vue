<template>
  <div id="bottomRight">
    <!-- <div class="d-flex pt-2 pl-2">
      <span style="color:#5cd9e8">
        <icon name="chart-pie"></icon>
      </span>
      <div class="d-flex">
        <span class="fs-xl text mx-2">服务器生产年份分布</span>
      </div>
    </div> -->
    <div class="bottom-charts">
      <div class="bc-chart-item">
        <div class="bcci-header">数据集群1</div>
        <div class="bcci-header">总数:{{siteData}}台</div>
        <dv-active-ring-chart :config="config1" />
        <Label-Tag :config="labelConfig" />
        
      </div>
      <dv-decoration-2 class="decoration-1" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">数据集群2</div>
        <div class="bcci-header">总数:{{clusterData}}台</div>
        <dv-active-ring-chart :config="config2" />
        <Label-Tag :config="labelConfig" />
      </div>

      <dv-decoration-2 class="decoration-2" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">数据集群3</div>
        <div class="bcci-header">总数:{{hypervisorData}}台</div>
        <dv-active-ring-chart :config="config3" />
        <Label-Tag :config="labelConfig" />
      </div>

      <dv-decoration-2 class="decoration-3" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">数据集群4</div>
        <div class="bcci-header">总数:{{physicalData}}台</div>
        <dv-active-ring-chart :config="config4" />
        <Label-Tag :config="labelConfig" />
      </div>

      <dv-decoration-2 class="decoration-4" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">数据集群5</div>
        <div class="bcci-header">总数:{{vmData}}台</div>
        <dv-active-ring-chart :config="config5" />
        <Label-Tag :config="labelConfig" />
      </div>

    </div>
  </div>
</template>

<script>
import LabelTag from './LabelTag'

export default {
  name: 'BottomCharts',
  components: {
    LabelTag
  },
  data () {
    return {
      siteData:661,
      clusterData:1135,
      hypervisorData:1297,
      physicalData:661,
      vmData:1110,
      config1: {
        data: [
          {
            name: '主机1',
            value: 356
          },
          {
            name: '主机2',
            value: 215
          },
          {
            name: '主机3',
            value: 90
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config2: {
        data: [
          {
            name: '主机2',
            value: 615
          },
          {
            name: '主机2',
            value: 322
          },
          {
            name: '主机3',
            value: 198
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config3: {
        data: [
          {
            name: '主机1',
            value: 452
          },
          {
            name: '主机2',
            value: 512
          },
          {
            name: '主机3',
            value: 333
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config4: {
        data: [
          {
            name: '主机1',
            value: 156
          },
          {
            name: '主机2',
            value: 415
          },
          {
            name: '主机3',
            value: 90
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config5: {
        data: [
          {
            name: '主机1',
            value: 234
          },
          {
            name: '主机2',
            value: 222
          },
          {
            name: '主机3',
            value: 654
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      labelConfig: {
        data: ['主机1', '主机2', '主机3']
      }
    }
  }
}
</script>

<style lang="scss">
#bottomRight {
  padding: 0.2rem 0.2rem 0;
  height: 5.5rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .bottom-charts {
    width: 100%;
    height: 100%;
    display: flex;
    position: relative;

    .bc-chart-item {
      width: 20%;
      height: 100%;
      padding-top: 20px;
      box-sizing: border-box;
    }

    .bcci-header {
      height: 50px;
      text-align: center;
      line-height: 50px;
      font-size: 20px;
    }

    .dv-active-ring-chart {
      height: 65%;
    }

    .label-tag {
      height: 30px;
    }

    .active-ring-name {
      font-size: 16px !important;
    }

    .decoration-1, .decoration-2, .decoration-3, .decoration-4 {
      display: absolute;
      left: 0%;
    }
  }
}
</style>
