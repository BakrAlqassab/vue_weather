<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ?'warm': typeof weather.main != 'undefined' && weather.main.temp < 3 ? 'freeze': '' ">
    <main>
      <div class="search-box">
        <input
          type="text"
          name=""
          class="search-bar"
          placeholder="Search..."
          v-model="query"
          @keypress="fetchWeather"
        />
        <!-- v-on:keypress='fetch' -->
        <!-- {{ query }} -->
      </div>
      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">{{ weather.name }},{{weather.sys.country}}</div>
          <div class="date">{{dateBuilder()}}</div>
        </div>

        <div class="weather-box">
          <!-- press alt + 0176 to have temp degree sign  -->
          <div class="temp">{{Math.round(weather.main.temp)}}</div>
          <div class="weather">{{weather.weather[0].main}}</div>
        </div>
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
      api_key: "ENTER YOUR API KEY HERE ",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(
          // for using fehrinhite degree just delete the units=metric
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then((response) => response.json())
          .then(this.setResults);
      }
    },
    setResults(result) {
      // the 'result' here represent the responding data from the api
      this.weather = result;
    },
    dateBuilder(){
      let d = new Date();
      let months = ["January","Febrauary","March","April","May","June","July","Augest",
      "Septemper","October","November","December"];
      let days =["Sunday","Monday","Tuesday","Wenesday","Theuresday","Friday","Saturday"];
    let day = days[d.getDay()];
    let date = d.getDate();
    let month = months[d.getMonth()];
    let year = d.getFullYear();
    return `${day} ${date} ${month} ${year}`

    }
  },
};
</script>

<style scoped src='./css/weather.css'>
</style>
