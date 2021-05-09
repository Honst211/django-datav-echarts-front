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
                data: ['料纹', '冲胶', '缺胶','脏印','缩水','漏线','开裂','针眼','杂色','压线'],
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
                    name: '料纹',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.material_grain
                },
                {
                    name: '冲胶',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.rubber_punching
                },
                {
                    name: '缺胶',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.lack_of_glue
                },
                {
                    name: '脏印',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.dirty_seal
                },
                {
                    name: '缩水',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.shrink
                },
                {
                    name: '漏线',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.leaky_line
                },
                {
                    name: '开裂',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.crack
                },
                {
                    name: '针眼',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.eye_of_needle
                },
                {
                    name: '杂色',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.variegated
                },
                {
                    name: '压线',
                    type: 'bar',
                    stack: '总量',
                    label: {
                        // show: true,
                        position: 'insideRight'
                    },
                    data: newData.line_pressing
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