<template>
  <div id="bottomLeft">
    <div class="up">
      <div class="item bg-color-black" v-for="item in titleItem" :key="item.title">
          <p class="ml-5 colorBlue fw-b">{{item.title}}</p>
          <div>
          <dv-digital-flop :config="item.number" style="width:3rem;height:.625rem;" />
          </div>
      </div>
    </div>
    <div class="down">
      <div class="percent bg-color-black">
        <div class="item">
          <span>上午失败率(/100)</span>
          <BottomChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />
        </div>
        <div class="item">
          <span>下午失败率(/100)</span>
          <BottomChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />
        </div>
        <div class="item">
          <span>加班失败率(/100)</span>
          <BottomChart :id="rate[0].id" :tips="rate[2].tips" :colorObj="rate[0].colorData" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BottomChart from "@/components/echart/bottom/bottomLeftChart";
export default {
  data() {
    return {
        titleItem: [
            {
            title: "上午生产总数(千台)",
            number: {
                number: [],
                toFixed: 3,
                content: "{nt}"
            }
            },
            {
            title: "下午生产总数(千台)",
            number: {
                number: [],
                toFixed: 3,
                content: "{nt}"
            }
            },
            {
            title: "加班生产总数(千台)",
            number: {
                number: [],
                toFixed: 3,
                content: "{nt}"
            }
            },
            {
            title: "上午生产失败总数(千台)",
            number: {
                number: [],
                toFixed: 3,
                content: "{nt}"
            }
            },
            {
            title: "下午生产失败总数(千台)",
            number: {
                number: [],
                toFixed: 3,
                content: "{nt}"
            }
            },
            {
            title: "加班生产失败总数(千台)",
            number: {
                number: [],
                toFixed: 1,
                content: "{nt}"
            }
            }
        ],
      // 通过率和达标率的组件复用数据
      rate: [
        {
          id: "centerRate1",
          tips: 0,
          colorData: {
            textStyle: "#3fc0fb",
            series: {
              color: ["#00bcd44a", "transparent"],
              dataColor: {
                normal: "#03a9f4",
                shadowColor: "#97e2f5"
              }
            }
          }
        },
        {
          id: "centerRate2",
          tips: 0,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad"
              }
            }
          }
        },
        {
          id: "centerRate3",
          tips: 0,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad"
              }
            }
          }
        }
      ]
    };
  },
  components: {
      BottomChart
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData () {
      let _Rthis  = this;
      this.axios.get("/api/bottomLeftView/").then(function(res){
        if(res.data.code == 200){
          _Rthis.titleItem[0]['number']['number'].push(res.data.data['上午']['yield_d'] / 1000) 
          _Rthis.titleItem[1]['number']['number'].push(res.data.data['下午']['yield_d'] / 1000)
          _Rthis.titleItem[2]['number']['number'].push(res.data.data['加班']['yield_d'] / 1000)
          _Rthis.titleItem[3]['number']['number'].push(res.data.data['上午']['bad_quantity'] / 1000)
          _Rthis.titleItem[4]['number']['number'].push(res.data.data['下午']['bad_quantity']/ 1000)
          _Rthis.titleItem[5]['number']['number'].push(res.data.data['加班']['bad_quantity'] / 1000)
          _Rthis.rate[0]['tips'] = parseFloat(res.data.data['上午']['defective_rate_r']) * 100
          _Rthis.rate[1]['tips'] = parseFloat(res.data.data['下午']['defective_rate_r']) * 100
          _Rthis.rate[2]['tips'] = parseFloat(res.data.data['加班']['defective_rate_r']) * 100

          _Rthis.titleItem[0].number = { ..._Rthis.titleItem[0].number }
          _Rthis.titleItem[1].number = { ..._Rthis.titleItem[1].number }
          _Rthis.titleItem[2].number = { ..._Rthis.titleItem[2].number }
          _Rthis.titleItem[3].number = { ..._Rthis.titleItem[3].number }
          _Rthis.titleItem[4].number = { ..._Rthis.titleItem[4].number }
          _Rthis.titleItem[5].number = { ..._Rthis.titleItem[5].number }
        }
      })
      .catch(function(error){
        console.log(error)
      })
    }
  }
};
</script>

<style lang="scss">
#bottomLeft {
  padding: 0.2rem 0rem;
  height: 5.5rem;
  min-width: 3.75rem;
  border-radius: 0.0625rem;
  .up {
    padding: 0rem 0.2rem;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 0.0625rem;
      padding-top: 0.1rem;
      margin-top: 0.2rem;
      width: 48%;
      height: 0.875rem;
    }
  }
  .down {
    padding: 0.1rem 0.2rem;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 2rem;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 0.0625rem;
    }
    .ranking {
      padding: 0.125rem;
      width: 59%;
    }
    .percent {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 32%;
        height: 1.5rem;
        span {
          margin-top: 0.0875rem;
          display: flex;
          justify-content: center;
        }
      }
    }
  }
}
</style>