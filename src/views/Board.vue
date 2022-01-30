<template>
  <div>

    <img src="../assets/aqua.jpg" class="bgImage">

    <h1>Coming Soon Board</h1>

    <v-row class="clockWeather">
      <v-col><Clock /></v-col>
      <v-col><Weather /></v-col>
    </v-row>

      <v-simple-table dark>
    <!-- <template v-slot:default> -->
      <thead>
        <tr>
          <th class="text-left">
            제목
          </th>
          <th class="text-left">
            작성자
          </th>
          <th class="text-left">
            작성일자
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="post in posts"
          :key="post.title"
        >
          <td>{{ post.title }}</td>
          <td>{{ post.user }}</td>
          <td>{{ post.date }}</td>
        </tr>
      </tbody>
    <!-- </template> -->
  </v-simple-table>

  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Clock from "../components/Clock.vue"; // @ is an alias to /src
import Weather from "../components/Weather.vue";

export default Vue.extend({
  name: "Home",
  components: {
    Clock,
    Weather,
  },
data () {
      return {
        posts: [
          {
            title: '난장판?',
            user: '이지롱',
            date: '2022-01-30 / 11:55:59'
          },
          {
            title: '초밥',
            user: '먹고싶다',
          },
        ],
      }
    },
});
</script>

<style scope>
  .clockWeather {
    font-size: 30px;
  }

  .bgImage {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  animation: fadeIn 0.5s linear;
}
</style>