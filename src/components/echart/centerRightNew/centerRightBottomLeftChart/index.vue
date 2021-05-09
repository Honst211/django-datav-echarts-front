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
        PCB_board: [],
        wire_rod: [],
        SP: [],
        air_traffic_control: [],
        gluing: [],
        f_2C: [],
        f_5C: [],
        f_2C_leakage: [],
        f_5C_leakage: [],
        core_wire: [],
        size: [],
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
      this.axios.get("/api/centerRight03View/").then(function(res){
        if(res.data.code == 200){
          _Rthis.cdata.category = res.data.data['date']
          _Rthis.cdata.PCB_board = res.data.data['PCB_board']
          _Rthis.cdata.wire_rod = res.data.data['wire_rod']
          _Rthis.cdata.SP = res.data.data['SP']
          _Rthis.cdata.air_traffic_control = res.data.data['air_traffic_control']
          _Rthis.cdata.f_2C = res.data.data['f_2C']
          _Rthis.cdata.f_5C = res.data.data['f_5C']
          _Rthis.cdata.f_2C_leakage = res.data.data['f_2C_leakage']
          _Rthis.cdata.f_5C_leakage = res.data.data['f_5C_leakage']
          _Rthis.cdata.core_wire = res.data.data['core_wire']
          _Rthis.cdata.size = res.data.data['size']
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