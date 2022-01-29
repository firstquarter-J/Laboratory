<template>
    <div class="home">
        <img
            class="bgImage"
            src="../assets/cosmic.jpg"
        />
        <p>{{ welcomeText }}</p>
        <p>
            <span class="red">난</span>
            <span class="orange">장</span>
            <span class="yellow">판</span>
            <span class="green"> 실</span>
            <span class="powderblue">험</span>
            <span class="violet">실</span>
        </p>
        <!-- <HelloWorld msg="난장판 실험실" /> -->

        <HelloWorld />
        <Weather />
        <Clock />
    </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "../components/HelloWorld.vue"; // @ is an alias to /src
import Clock from "../components/Clock.vue"; // @ is an alias to /src
// import Weather from "@/components/Weather.vue";
import Weather from "../components/Weather.vue";

export default Vue.extend({
    name: "Home",
    components: {
        HelloWorld,
        Clock,
        Weather,
    },
    data() {
        return {
            welcomeText: "오리가 얼면? 언덕",
        };
    },
});
</script>

<style scoped>
.bgImage {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    animation: fadeIn 0.5s linear;
}
span {
    font-size: 88px;
}
.red {
    color: rgb(214, 1, 1);
}
.orange {
    color: rgb(218, 147, 17);
}
.yellow {
    color: rgb(209, 209, 41);
}
.green {
    color: rgb(19, 207, 19);
}
.powderblue {
    color: rgb(10, 73, 192);
}
.violet {
    color: rgb(128, 2, 128);
}
</style>