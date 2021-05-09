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
        short_circuit: [],
        open_circuit: [],
        insulation: [],
        copper_wire_mix_and_match: [],
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
      this.axios.get("/api/centerRight04View/").then(function(res){
        if(res.data.code == 200){
          _Rthis.cdata.category = res.data.data['date']
          _Rthis.cdata.short_circuit = res.data.data['short_circuit']
          _Rthis.cdata.open_circuit = res.data.data['open_circuit']
          _Rthis.cdata.insulation = res.data.data['insulation']
          _Rthis.cdata.copper_wire_mix_and_match = res.data.data['copper_wire_mix_and_match']
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