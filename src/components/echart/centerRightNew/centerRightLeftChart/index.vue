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
        false_welding: [],
        continuous_tin: [],
        deviation: [],
        broken_copper: [],
        tin_beads: [],
        fuzzing: [],
        reverse_line: [],
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
      this.axios.get("/api/centerRight01View/").then(function(res){
        if(res.data.code == 200){
          _Rthis.cdata.category = res.data.data['date']
          _Rthis.cdata.false_welding = res.data.data['false_welding']
          _Rthis.cdata.continuous_tin = res.data.data['continuous_tin']
          _Rthis.cdata.deviation = res.data.data['deviation']
          _Rthis.cdata.broken_copper = res.data.data['broken_copper']
          _Rthis.cdata.tin_beads = res.data.data['tin_beads']
          _Rthis.cdata.fuzzing = res.data.data['fuzzing']
          _Rthis.cdata.reverse_line = res.data.data['reverse_line']
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