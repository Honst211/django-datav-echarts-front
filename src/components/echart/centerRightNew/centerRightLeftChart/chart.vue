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
                    data: ['假焊', '连锡', '偏位', '断铜', '锡珠', '起毛', '反线'],
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
                        name: '假焊',
                        type: 'bar',
                        data: newData.false_welding
                    },
                    {
                        name: '连锡',
                        type: 'bar',
                        data: newData.continuous_tin
                    },
                    {
                        name: '偏位',
                        type: 'bar',
                        data: newData.deviation
                    },
                    {
                        name: '断铜',
                        type: 'bar',
                        data: newData.broken_copper
                    },
                    {
                        name: '锡珠',
                        type: 'bar',
                        data: newData.tin_beads
                    },
                    {
                        name: '起毛',
                        type: 'bar',
                        data: newData.fuzzing
                    },
                    {
                        name: '反线',
                        type: 'bar',
                        data: newData.reverse_line
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