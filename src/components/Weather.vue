<template>
  <div class="weather">
    <h1>{{ getWeather }}</h1>
    <h1>{{ weather }}</h1>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Weather",
  data() {
    return {
      API_KEY: "761047b11b9ee4554c537e1d7f91fdf4",
      COORDS: "coords",
      weather: "여기는 날씨",
    };
  },
  mounted() {
    this.loadCoords();
  },
  computed: {},
  methods: {
    askForCoords() {
      const getCurrentPositionOptions = {
        enableHighAccuracy: true,
        timeout: 5000,
        maximumAge: 0,
      };
      navigator.geolocation.getCurrentPosition(
        this.handleGeoSuccess,
        this.handleGeoError,
        getCurrentPositionOptions
      );
    },
    handleGeoSuccess(position: Record<any, any>) {
      // console.log("석세스 포지션", position);
      // console.log(typeof position);
      // const positionCoords = position.coords;
      const latitude = position.coords.latitude;
      const longitude = position.coords.longitude;
      // console.log(typeof position.coords.latitude);
      // console.log(latitude, longitude);
      const coordsObj = {
        latitude,
        longitude,
      };
      this.saveCoords(coordsObj);
    },
    handleGeoError() {
      console.log(`Can't Access Geo Location!!!`);
    },
    saveCoords(coordsObj: Record<string, string>) {
      localStorage.setItem(this.COORDS, JSON.stringify(coordsObj));
      this.loadCoords();
    },
    loadCoords() {
      const loadedCords = localStorage.getItem(this.COORDS);
      console.log(loadedCords);
      if (loadedCords === null) {
        this.askForCoords();
      } else {
        const parsedCoords = JSON.parse(loadedCords);
        this.getWeather(parsedCoords.latitude, parsedCoords.longitude);
      }
    },
    getWeather(lat: string, lon: string) {
      fetch(
        `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${this.API_KEY}&units=metric`
      )
        .then(function (response) {
          return response.json();
        })
        .then(function (json) {
          const temperature = json.main.temp;
          const place = json.name;
          const weather = `${temperature}℃
        ${place}
        `;
          //   this.weather = `${temperature}℃
          // ${place}
          // `;
          console.log(weather);
          return `${temperature}℃
        ${place}
        `;
        });
    },
  },
});
</script>

<style scoped>
h1 {
  font-size: 88px;
  color: rgb(5, 56, 199);
}
</style>

