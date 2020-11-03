<template>
  <h1>Feels like {{feelsLike}}</h1>

</template>

<script>
export default {
  data () {
    return {
      weatherData: fetch('https://api.openweathermap.org/data/2.5/weather?zip=11418,us&units=imperial&appid=c93956b233247d73e54794d4d5d1d5d8')
        .then(async res => {
          let json = await res.json()
          return json
        }).catch(e => console.log(e.message)),
      feelsLike: ''
    }
  },
  created () {
    this.weatherData.then(wData => {
      this.feelsLike = wData.main.feels_like
    })
    // const weatherData = fetch('https://api.openweathermap.org/data/2.5/weather?zip=11418,us&appid=c93956b233247d73e54794d4d5d1d5d8')
    //                           .then( async res => {
    //                             return await res.json()
    //                           }).catch(e => console.log(e.message))
  }
}
</script>

<style lang="css" scoped>
</style>
