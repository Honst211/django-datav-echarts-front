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
        <div class="bcci-header">12车间PCB板外检工段</div>
        <dv-active-ring-chart :config="config1" />
        <Label-Tag :config="labelConfig" />
        
      </div>
      <dv-decoration-2 class="decoration-1" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">成型车间SP外检工段</div>
        <dv-active-ring-chart :config="config2" />
        <Label-Tag :config="labelConfig" />
      </div>

      <dv-decoration-2 class="decoration-2" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">电子车间外检工段</div>
        <dv-active-ring-chart :config="config3" />
        <Label-Tag :config="labelConfig" />
      </div>

      <dv-decoration-2 class="decoration-3" :reverse="true" style="width:5px;" />

      <div class="bc-chart-item">
        <div class="bcci-header">电子车间测试工段</div>
        <dv-active-ring-chart :config="config4" />
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
      config1: {
        data: [],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config2: {
        data: [],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config3: {
        data: [],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      config4: {
        data: [],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
        radius: '65%',
        activeRadius: '70%',
        showOriginValue: true
      },

      labelConfig: {
        data: ['上午', '下午', '加班']
      }
    }
  },
  mounted () {
    this.getData();
  },
  methods: {
    getData () {
      let _Rthis  = this;
      this.axios.get("/api/bottomRightView/").then(function(res){
        if(res.data.code == 200){
          _Rthis.config1.data = res.data.data['12车间PCB板外检工段']
          _Rthis.config2.data = res.data.data['成型车间SP外检工段']
          _Rthis.config3.data = res.data.data['电子车间外检工段']
          _Rthis.config4.data = res.data.data['电子车间测试工段']

          _Rthis.config1 = { ..._Rthis.config1 }
          _Rthis.config2 = { ..._Rthis.config2 }
          _Rthis.config3 = { ..._Rthis.config3 }
          _Rthis.config4 = { ..._Rthis.config4 }
        }
      })
      .catch(function(error){
        console.log(error)
      })
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
      width: 25%;
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
      height: 60%;
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
