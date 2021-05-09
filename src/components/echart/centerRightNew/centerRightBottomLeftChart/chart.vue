<template>
  <div>
    <Echart
      :options="options"
      id="centerRightRightChart"
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
                axisPointer: {            // 坐标轴指示器，坐标轴触发有效
                    type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
                }
            },
            legend: {
                data: ['PCB板', '线材', 'SP','空管','沾胶','2C','5C','2C漏沾','5C漏沾','芯线','尺寸'],
                type:'scroll',
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
                    name: 'PCB板',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.PCB_board
                },
                {
                    name: '线材',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.wire_rod
                },
                {
                    name: 'SP',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.SP
                },
                {
                    name: '空管',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.air_traffic_control
                },
                {
                    name: '沾胶',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.gluing
                },
                {
                    name: '2C',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.f_2C
                },
                {
                    name: '5C',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.f_5C
                },
                {
                    name: '2C漏沾',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.f_2C_leakage
                },
                {
                    name: '5C漏沾',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.f_5C_leakage
                },
                {
                    name: '芯线',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.core_wire
                },
                {
                    name: '产量',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.size
                },
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