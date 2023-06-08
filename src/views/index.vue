<template>
  <div id="index">
    <dv-full-screen-container class="bg">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 style="width:33.3%;height:5px;" />
          <div class="d-flex jc-center">
            <dv-decoration-8 :color="['#568aea', '#000000']" style="width:200px;height:50px;" />
            <div class="title">
              <span class="title-text">大数据可视化平台</span>
              <dv-decoration-6
                class="title-bototm"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
                style="width:250px;height:8px;"
              />
            </div>
            <dv-decoration-8
              :reverse="true"
              :color="['#568aea', '#000000']"
              style="width:200px;height:50px;"
            />
          </div>
          <dv-decoration-10 style="width:33.3%;height:5px;" />
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex" style="width: 40%">
            <div
              class="react-right ml-4"
              style="width: 500px; text-align: left;background-color: #0f1325;"
            >
              <span class="react-before"></span>
              <span class="text fw-b">数据分析1</span>
            </div>
            <div class="react-right ml-3" style="background-color: #0f1325;">
              <span class="text colorBlue fw-b">数据分析2</span>
            </div>
          </div>
          <div style="width: 40%" class="d-flex">
            <div class="react-left bg-color-blue mr-3">
              <span class="text fw-b">数据分析3</span>
            </div>
            <div
              class="react-left mr-4"
              style="width: 500px; background-color: #0f1325; text-align: right;"
            >
              <span class="react-after"></span>
              <span class="text">{{currentTime}}</span>
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-12>
                <centreLeft1 />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12>
                <centreLeft2 />
              </dv-border-box-12>
            </div>
            <div>
              <center />
            </div>
            <div>
              <centreRight2 />
            </div>
            <div>
              <dv-border-box-13>
                <centreRight1 />
              </dv-border-box-13>
            </div>
          </div>

          <!-- 第四行数据 -->
          <!-- <div class="bototm-box">
            <dv-border-box-13>
              <bottomLeft />
            </dv-border-box-13>
            <dv-border-box-12>
              <bottomRight />
            </dv-border-box-12>
          </div> -->
        </div>
      </div>
    </dv-full-screen-container>
  </div>
</template>

<script>
import centreLeft1 from "./centreLeft1";
import centreLeft2 from "./centreLeft2";
// import centreRight1 from "./centreRight1";
// import centreRight2 from "./centreRight2";
// import center from "./center";
// import bottomLeft from "./bottomLeft";
// import bottomRight from "./bottomRight";
export default {
  data() {
    return {
      loading: true,
      currentTime: ''
    };
  },
  components: {
    centreLeft1,
    centreLeft2,
    // centreRight1,
    // centreRight2,
    // center,
    // bottomLeft,
    // bottomRight
  },
  mounted() {
    this.cancelLoading();
    this.updateCurrentTime();
  },
  methods: {
    cancelLoading() {
      setTimeout(() => {
        this.loading = false;
      }, 2000);
    },
    updateCurrentTime() {
      setInterval(() => {
        this.getCurrentTime()
      }, 1000);
    },
    getCurrentTime() {
      function repair(i){
        if (i >= 0 && i <= 9) {
            return "0" + i;
        } else {
            return i;
        }
      }

      let date = new Date();//当前时间
      let year = date.getFullYear() //返回指定日期的年份
      let month = repair(date.getMonth() + 1);//月
      let day = repair(date.getDate());//日
      let hour = repair(date.getHours());//时
      let minute = repair(date.getMinutes());//分
      let second = repair(date.getSeconds());//秒
      
      //当前时间 
      let curTime = year + "-" + month + "-" + day + " " + hour + ":" + minute + ":" + second;
      this.currentTime = curTime
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/index.scss";
</style>