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
                    data: ['短路', '断路', '绝缘', '铜丝混搭'],
                    type:'scroll',
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
                        name: '短路',
                        type: 'bar',
                        data: newData.short_circuit
                    },
                    {
                        name: '断路',
                        type: 'bar',
                        data: newData.open_circuit
                    },
                    {
                        name: '绝缘',
                        type: 'bar',
                        data: newData.insulation
                    },
                    {
                        name: '铜丝混搭',
                        type: 'bar',
                        data: newData.copper_wire_mix_and_match
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