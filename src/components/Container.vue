<template>
  <div class="container">
    <form class="" action="javascript:undefined;">
      <input type="text" name="location" value="">
      <button type="button" name="button">Go</button>
    </form>
    <weather-info :location="locationObj"/>
  </div>
</template>

<script>
import WeatherInfo from './WeatherInfo'
export default {
  data () {
    return {
      locationObj: {
        zip: '11418'
      }
      // weatherData: fetch('https://api.openweathermap.org/data/2.5/weather?zip=11418,us&units=imperial&appid=c93956b233247d73e54794d4d5d1d5d8')
      //   .then(async res => {
      //     let json = await res.json()
      //     return json
      //   }).catch(e => console.log(e.message)),
      // feelsLike: '',
      // currentTemp: '',
      // highTemp: '',
      // lowTemp: '',
      // desc: '',
      // icon: '',
      // name: ''
    }
  },
  components: {
    weatherInfo: WeatherInfo
  },
  methods: {
    getLocation: () => {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(res => {
          console.log(res)
        }, console.log('Unable to get geolocation.'))
      } else {
        console.log('Geolocation is not supported by this browser.')
      }
    }
  },
  created () {
    this.getLocation()
    // this.weatherData.then(wData => {
    //   console.log(wData)
    //   this.feelsLike = Math.round(wData.main.feels_like) + 'º'
    //   this.currentTemp = Math.round(wData.main.temp) + 'º'
    //   this.highTemp = Math.round(wData.main.temp_max) + 'º'
    //   this.lowTemp = Math.round(wData.main.temp_min) + 'º'
    //   this.desc = wData.weather[0].description.toUpperCase()
    //   this.icon = `http://openweathermap.org/img/wn/${wData.weather[0].icon}@4x.png`
    //   this.name = wData.name
    // })
    // const weatherData = fetch('https://api.openweathermap.org/data/2.5/weather?zip=11418,us&appid=c93956b233247d73e54794d4d5d1d5d8')
    //                           .then( async res => {
    //                             return await res.json()
    //                           }).catch(e => console.log(e.message))
  }
}
</script>

<style lang="css" scoped>
</style>
