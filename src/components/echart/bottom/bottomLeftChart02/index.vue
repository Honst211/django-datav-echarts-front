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
        category: [
        ],
        lineData: [
        ],
        barData: [
        ],
        rateData: []
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
      this.axios.get("/api/centerLeftView/").then(function(res){
        if(res.data.code == 200){
          _Rthis.cdata.category = res.data.data.category
          _Rthis.cdata.lineData = res.data.data.lineData
          _Rthis.cdata.barData = res.data.data.barData

          for (let i = 0; i < res.data.data.barData.length -1; i++) {
            let rate = res.data.data.barData[i] / res.data.data.lineData[i] * 100;
            _Rthis.cdata.rateData.push(rate.toFixed(2));
          }
        }
      })
      .catch(function(error){
        console.log(error)
      })
    },
  }
};
</script>

<style lang="scss" scoped>
</style>