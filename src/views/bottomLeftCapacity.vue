<template>
  <div id="bottomLeft">
    <div class="up">
      <div class="item bg-color-black" v-for="item in titleItem" :key="item.title">
          <p class="ml-3 colorBlue fw-a">{{item.title}}</p>
          <div>
          <dv-digital-flop :config="item.number" style="width:1.5rem;height:.625rem;" />
          </div>
      </div>
    </div>
    <div class="down">
      <div class="percent bg-color-black">
        <div class="item">
          <span>全球数据使用率1</span>
          <BottomChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />
        </div>
        <div class="item">
          <span>全球数据使用率2</span>
          <BottomChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />
        </div>
        <div class="item">
          <span>全球数据使用率3</span>
          <BottomChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />
        </div>
        <div class="item">
          <span>全球数据使用率4</span>
          <BottomChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />
        </div>
        <div class="item">
          <span>全球数据使用率5</span>
          <BottomChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />
        </div>
        <div class="item">
          <span>全球数据使用率6</span>
          <BottomChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BottomChart from "@/components/echart/bottom/bottomLeftChart";
export default {
  data() {
    return {
        titleItem: [
            {
            title: "数据T1",
            number: {
                number: [49],
                toFixed: 1,
                content: "{nt}"
            }
            },
            {
            title: "数据T2",
            number: {
                number: [43],
                toFixed: 1,
                content: "{nt}"
            }
            },
            {
            title: "数据T3",
            number: {
                number: [36],
                toFixed: 1,
                content: "{nt}"
            }
            },
            {
            title: "数据T4",
            number: {
                number: [142.3],
                toFixed: 1,
                content: "{nt}"
            }
            },
            {
            title: "数据T5",
            number: {
                number: [106],
                toFixed: 1,
                content: "{nt}"
            }
            },
            {
            title: "数据T6",
            number: {
                number: [100],
                toFixed: 1,
                content: "{nt}"
            }
            }
        ],
      // 通过率和达标率的组件复用数据
      rate: [
        {
          id: "centerRate1",
          tips: 60,
          colorData: {
            textStyle: "#3fc0fb",
            series: {
              color: ["#00bcd44a", "transparent"],
              dataColor: {
                normal: "#03a9f4",
                shadowColor: "#97e2f5"
              }
            }
          }
        },
        {
          id: "centerRate2",
          tips: 40,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad"
              }
            }
          }
        }
      ]
    };
  },
  components: {
      BottomChart
  },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#bottomLeft {
  padding: 0.2rem 0rem;
  height: 5.5rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .up {
    padding: 0rem 0.2rem;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 0.0625rem;
      padding-top: 0.1rem;
      margin-top: 0.1rem;
      width: 32%;
      height: 0.875rem;
    }
  }
  .down {
    padding: 0.1rem 0.2rem;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 3.1875rem;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 0.0625rem;
    }
    .ranking {
      padding: 0.125rem;
      width: 59%;
    }
    .percent {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 33%;
        height: 1.5rem;
        span {
          margin-top: 0.0875rem;
          display: flex;
          justify-content: center;
        }
      }
    }
  }
}
</style>