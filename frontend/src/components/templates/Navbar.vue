<template>
  <div>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Page title</v-toolbar-title>

      <v-spacer></v-spacer>
      <span
        >{{ Math.round(currentWeather.main.temp) }} &#176;C
        {{ currentWeather.name }}</span
      >
      <!-- <v-btn icon> -->
      <!-- <v-icon>{{ currentWeather.name }}</v-icon> -->
      <!-- </v-btn> -->

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item v-for="n in 5" :key="n" @click="() => {}">
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      currentWeather: [],
    };
  },
  mounted() {
    axios
      .get(
        "http://api.openweathermap.org/data/2.5/weather?lat=47.8508&lon=35.1183&units=metric&appid="
      )
      .then((response) => (this.currentWeather = response.data));
  },
};
</script>
