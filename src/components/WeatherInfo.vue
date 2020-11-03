<template >
  <div class="weather-info">
    <img :src="icon">
    <h1>{{name}}</h1>
    <h1><i>{{currentTemp}}</i></h1>
    <b>{{desc}}</b>
    <h3><i>Feels like {{feelsLike}}</i></h3>
  </div>
</template>

<script>
export default {
  props: [
    'location'
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
  created () {
    console.log(this.location)
    fetch('https://api.openweathermap.org/data/2.5/weather?zip=11418,us&units=imperial&appid=' + this.API_KEY)
      .then(async res => {
        let json = await res.json()
        console.log(json)
        return json
      }).catch(e => console.log(e.message))
  }
}
</script>

<style lang="css" scoped>
</style>
