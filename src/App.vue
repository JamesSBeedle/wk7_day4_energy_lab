<template>
  <div id="app">
    <h1>UK National Energy Usage Sources</h1>
    <div>

    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      rawEnergyData: [],
      translatedEnergyData: [],
      // startTime: null,
      // endTime: null,
    }
  },
  components: {

  },
  mounted() {
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(res => res.json())
    .then(data => this.rawEnergyData = data.data.generationmix)
    // .then(data => this.startTime = data.data.from)
    // .then(data => this.endTime = data.data.to)
  }
}
</script>

<style>

</style>
