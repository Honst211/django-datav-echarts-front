<template>
  <div id="centerRightPillars">
    <div class="bc-height-chart-item">
        <div class="center-charts"> 
            <div class="bc-width-chart-item-top">
                <div class="d-flex pt-2 pl-2">
                    <span style="color:#5cd9e8">
                        <icon name="chart-bar"></icon>
                    </span>
                    <div class="d-flex">
                        <span class="fs-xl text mx-2">12车间PCB板外检工段</span>
                    </div>
                </div>
                <centerRightLeftChart/>
            </div>
            <dv-decoration-2 :reverse="true" style="display: absolute;left: 0%;width:5px;" />
            <div class="bc-width-chart-item-top">
                <div class="d-flex pt-2 pl-2">
                    <span style="color:#5cd9e8">
                        <icon name="chart-bar"></icon>
                    </span>
                    <div class="d-flex">
                        <span class="fs-xl text mx-2">成型车间SP外检工段</span>
                    </div>
                </div>
                <centerRightRightChart/>
            </div>
        </div>
    </div>

    <dv-decoration-2 style="height:10px;" />

    <div class="bc-height-chart-item">
        <div class="center-charts"> 
            <div class="bc-width-chart-item-top">
                <div class="d-flex pt-2 pl-2">
                    <span style="color:#5cd9e8">
                        <icon name="chart-bar"></icon>
                    </span>
                    <div class="d-flex">
                        <span class="fs-xl text mx-2">电子车间外检工段</span>
                    </div>
                </div>
                <centerRightBottomLeftChart/>
            </div>
            <dv-decoration-2 :reverse="true" style="display: absolute;left: 0%;width:5px;" />
            <div class="bc-width-chart-item-top">
                <div class="d-flex pt-2 pl-2">
                    <span style="color:#5cd9e8">
                        <icon name="chart-bar"></icon>
                    </span>
                    <div class="d-flex">
                        <span class="fs-xl text mx-2">电子车间测试工段</span>
                    </div>
                </div>
                <centerRightBottomRightChart/>
            </div>
        </div>
    </div>
    <!-- <div>
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2">柱状图</span>
      </div>

      <div class="d-flex jc-center body-box" style=" margin-top: 0;">
          
      </div>
    </div> -->
  </div>
</template>

<script>
import centerRightLeftChart from "@/components/echart/centerRightNew/centerRightLeftChart";
import centerRightRightChart from "@/components/echart/centerRightNew/centerRightRightChart";
import centerRightBottomLeftChart from "@/components/echart/centerRightNew/centerRightBottomLeftChart";
import centerRightBottomRightChart from "@/components/echart/centerRightNew/centerRightBottomRightChart";
export default {
  data() {
    return {
      config1: {
          data: [

          ]
      }
    };
  },
  components: {
      centerRightLeftChart,
      centerRightRightChart,
      centerRightBottomLeftChart,
      centerRightBottomRightChart

  },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#centerRightPillars {
  padding: 0.0625rem;
  height: 6.125rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .bg-color-black {
    padding: 0.0625rem;
    height: 6.125rem;
    border-radius: 0.125rem;
  }
  .text {
    color: #c3cbde;
  }
  .body-box {
    border-radius: 0.125rem;
    overflow: hidden;
  }
  .bc-height-chart-item {
      width: 100%;
      height: 45%;
      padding-top: 0px;
      box-sizing: border-box;
      .center-charts {
        width: 100%;
        height: 100%;
        display: flex;
        position: relative;
        .bc-width-chart-item-top {
            width:50%;
            height:100%;
            padding-top: 0px;
            box-sizing: border-box;
        }
      }
  }
}
</style>