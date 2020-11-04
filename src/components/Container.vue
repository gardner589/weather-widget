<template>
  <div class="container">
    <form class="location-form" action="javascript:undefined;" v-if="!locationType">
      <button type="button" name="getCurrentLocation" @click="getLocation()">Use Current Location</button>
      <h2>Or</h2>
      <div class="location-input">
        <input type="text" name="location" v-model="inputValue">
        <label for="location">City, State or Zip Code</label>
        <button type="button" name="submit" @click="formSubmit(inputValue)">Submit</button>
      </div>
    </form>
    <weather-info :locationInfo="locationObj" v-if="locationType"/>
  </div>
</template>

<script>
import WeatherInfo from './WeatherInfo'
export default {
  data () {
    return {
      locationObj: {},
      locationType: '',
      inputValue: ''

    }
  },
  components: {
    weatherInfo: WeatherInfo
  },
  methods: {
    getLocation: function () {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(res => {
          console.log(res.coords)
          this.locationType = 'geo'
          this.locationObj.type = 'geo'
          this.locationObj.lat = res.coords.latitude
          this.locationObj.long = res.coords.longitude
        }, console.log('Unable to get geolocation.'))
      } else {
        console.log('Geolocation is not supported by this browser.')
      }
    },
    formSubmit: function (val) {
      if (parseInt(val)) {
        this.locationType = 'zip'
        this.locationObj.zip = val
      } else if (val.split(',').length > 1) {
        this.locationType = 'city'
        this.locationObj.city = val.split(',')[0]
        this.locationObj.state = val.split(',')[1]
      } else {
        alert('Please enter city and state separated by comma or enter a zip code.')
      }
      this.locationObj.type = this.locationType
    }
  }
}
</script>

<style lang="css" scoped>
  .container {
    display: flex;
  }
  .location-form {
    display: flex;
    flex-direction: column;
  }
  .location-input {
    display: flex;
    flex-direction: column;
  }
</style>
