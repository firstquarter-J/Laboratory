<template>
    <div class="weather">
        <h1 class="temperature">{{ temperature }}</h1>
        <h1 class="place">{{ place }}</h1>
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
            place: "위치!",
            temperature: "온도!",
        };
    },
    mounted() {
        this.loadCoords();
    },
    computed: {
        handleGeoError() {
            return console.log(`Can't Access Geo Location!!!`);
        },
    },
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
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;
            const coordsObj = {
                latitude,
                longitude,
            };
            this.saveCoords(coordsObj);
        },
        saveCoords(coordsObj: Record<string, string>) {
            localStorage.setItem(this.COORDS, JSON.stringify(coordsObj));
            this.loadCoords();
        },
        loadCoords() {
            const loadedCords = localStorage.getItem(this.COORDS);
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
                .then((json) => {
                    const temperature = json.main.temp;
                    const place = json.name;
                    this.temperature = `${temperature}℃`;
                    this.place = `${place}`;
                });
        },
    },
});
</script>

<style scoped>
h1 {
    font-size: 88px;
}
.place {
    color: rgb(32, 255, 181);
}
.temperature {
    color: rgb(0, 0, 207);
}
</style>

