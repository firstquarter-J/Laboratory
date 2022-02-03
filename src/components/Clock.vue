<template>
  <div class="clock">
    <h1 class="yearMonthDay">{{ yearMonthDay }}</h1>
    <h1 class="time">{{ time }}</h1>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Clock",
  data() {
    return {
      yearMonthDay: "",
      time: "",
    };
  },
  mounted() {
    this.nowYearMonthDay();
    this.nowTime();
    setInterval(this.nowTime.bind(this), 1000);
    console.log(
      "Home->Clock mounted 가 왜 app.vue 콘솔보다 먼저 찍히지?>??????"
    );
  },
  methods: {
    setDate() {
      let year = new Date().getFullYear();
      let month =
        new Date().getMonth() + 1 < 10
          ? "0" + (new Date().getMonth() + 1)
          : new Date().getMonth() + 1;
      let date =
        new Date().getDate() < 10
          ? "0" + new Date().getDate()
          : new Date().getDate();
      let hour =
        new Date().getHours() < 10
          ? "0" + new Date().getHours()
          : new Date().getHours();
      let minute =
        new Date().getMinutes() < 10
          ? "0" + new Date().getMinutes()
          : new Date().getMinutes();
      let second =
        new Date().getSeconds() < 10
          ? "0" + new Date().getSeconds()
          : new Date().getSeconds();
      return {
        year,
        month,
        date,
        hour,
        minute,
        second,
      };
    },
    nowYearMonthDay() {
      this.yearMonthDay =
        this.setDate().year +
        "-" +
        this.setDate().month +
        "-" +
        this.setDate().date;
    },
    nowTime() {
      this.time = `${this.setDate().hour}
        :
        ${this.setDate().minute}
        :
        ${this.setDate().second}`;
    },
  },
});
</script>

<style scoped>
h1 {
  font-size: 88px;
}
.yearMonthDay {
  color: rgb(88, 186, 211);
}
.time {
  color: #ffc3fa;
}
</style>

