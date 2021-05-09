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
        category: [],
        material_grain: [],
        rubber_punching: [],
        lack_of_glue: [],
        dirty_seal: [],
        shrink: [],
        leaky_line: [],
        crack: [],
        eye_of_needle: [],
        variegated: [],
        line_pressing: [],
        other: [],
        clearance: [],
      }
    };
  },
  components: {
    Chart,
  },
  mounted () {
    this.getData();
  },
  methods: {
    getData () {
      let _Rthis  = this;
      this.axios.get("/api/centerRight02View/").then(function(res){
        if(res.data.code == 200){
          _Rthis.cdata.category = res.data.data['date']
          _Rthis.cdata.material_grain = res.data.data['material_grain']
          _Rthis.cdata.rubber_punching = res.data.data['rubber_punching']
          _Rthis.cdata.lack_of_glue = res.data.data['lack_of_glue']
          _Rthis.cdata.dirty_seal = res.data.data['dirty_seal']
          _Rthis.cdata.shrink = res.data.data['shrink']
          _Rthis.cdata.leaky_line = res.data.data['leaky_line']
          _Rthis.cdata.crack = res.data.data['crack']
          _Rthis.cdata.eye_of_needle = res.data.data['eye_of_needle']
          _Rthis.cdata.variegated = res.data.data['variegated']
          _Rthis.cdata.line_pressing = res.data.data['line_pressing']
          _Rthis.cdata.other = res.data.data['other']
          _Rthis.cdata.clearance = res.data.data['clearance']
        }
      })
      .catch(function(error){
        console.log(error)
      })
    }
  }
};
</script>

<style lang="scss" scoped>
</style>