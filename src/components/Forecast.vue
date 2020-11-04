<template>
  <div class="forecast-row">
    <h1>test</h1>

  </div>
</template>

<script>
export default {
  props: [
    'locationInfo'
  ],
  created () {
    console.log('lllllllllllllll')
    console.log(this.locationInfo)
    console.log('lllllllllllllll')
  }
}
</script>

<style lang="css" scoped>
  .forecast-row {
    outline: 1px solid red;
    width: 100%;
    position: absolute;
    left: -100vw;
    margin-left: 100%;
  }
</style>
