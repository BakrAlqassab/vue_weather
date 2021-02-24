<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div class="app">
    <main>
      <div class="search-box">
        <input
          type="text"
          name=""
          class="search-bar"
          placeholder="Search..."
          v-model="query"
        />
        {{ query }}
      </div>
      <div class="weather-wrap">
        <div class="location-box">
          <div class="location">Hämeenlinna,Finland</div>
          <div class="date">Wenesdy 24 Febrauary 2021</div>
        </div>
      </div>
      <div class="weather-box">
        <!-- press alt + 0176 to have temp degree sign  -->
        <div class="temp">9°C</div>
        <div class="weather">Snowing</div>
      </div>
    </main>
  </div>
</template>

<script>
import "./css/weather.css";
export default {
  name: "App",
  data() {
    return {
      api_key: "f77f4ec65ca8b253c15799a62d133e2d",
      url_base:'https://api.openweathermap.org/data/2.5/',
      query: "",
      weather:{},
    };
  },
  methods:{

    
  }
};
</script>

<style scoped src='./css/weather.css'>
</style>
