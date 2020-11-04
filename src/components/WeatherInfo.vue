<template>
  <div class="weather-info">
    <img :src="icon">
    <h1>{{name}}</h1>
    <b>{{desc}}</b>
    <h1><i>{{currentTemp}}</i></h1>
    <h3><i>Feels like {{feelsLike}}</i></h3>
    <!-- <forecast :locationInfo="locationInfo"/> -->
  </div>
</template>

<script>
// import Forecast from './Forecast.vue'
export default {
  props: [
    'locationInfo'
  ],
  data () {
    return {
      feelsLike: '',
      currentTemp: '',
      highTemp: '',
      lowTemp: '',
      desc: '',
      icon: '',
      name: ''
    }
  },
  methods: {
    getWeatherData: function (locData) {
      let url = ``
      if (this.locationInfo.type === 'city') {
        url = `https://api.openweathermap.org/data/2.5/weather?q=${locData.city},${locData.state},us&units=imperial&appid=${this.API_KEY}`
      }
      if (this.locationInfo.type === 'zip') {
        url = `https://api.openweathermap.org/data/2.5/weather?zip=${this.locationInfo.zip}&units=imperial&appid=${this.API_KEY}`
      }
      if (this.locationInfo.type === 'geo') {
        url = `https://api.openweathermap.org/data/2.5/weather?lat=${this.locationInfo.lat}&lon=${this.locationInfo.long}&units=imperial&appid=${this.API_KEY}`
      }

      fetch(url).then(async res => {
        let json = await res.json()
        this.feelsLike = Math.round(json.main.feels_like) + 'º'
        this.currentTemp = Math.round(json.main.temp) + 'º'
        this.highTemp = Math.round(json.main.temp_max) + 'º'
        this.lowTemp = Math.round(json.main.temp_min) + 'º'
        this.desc = json.weather[0].description.toUpperCase()
        this.icon = `http://openweathermap.org/img/wn/${json.weather[0].icon}@4x.png`
        this.name = json.name
      }).catch(e => console.log(e))
    }
  },
  created () {
    this.getWeatherData(this.locationInfo)
  },
  // components: {
  //   forecast: Forecast
  // }
}
</script>

<style lang="css">
  .weather-info {
    border: 1px solid black;
    box-shadow: 0 0 5px 1px;
    border-radius: 5px;
    padding: 1rem;
    background: aliceblue;
  }
  .weather-info > b {
    font-size: 0.8rem;
  }
  .weather-info > h1 {
    margin: .5rem;
  }
</style>
