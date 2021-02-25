<template>
  <div id="app">
    <h1>UK National Energy Usage Sources</h1>
    <energy-chart :rawEnergyData="rawEnergyData"></energy-chart>
  </div>
</template>

<script>
import EnergyChart from './components/EnergyChart.vue'

export default {
  name: 'App',
  data(){
    return {
      startTime: null,
      endTime: null,
      rawEnergyData: null,
    }
  },
  components: {
    'energy-chart': EnergyChart

  },
  mounted() {
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(res => res.json())
    .then(json => {
      this.startTime = json.data.from
      this.endTime = json.data.to
      this.rawEnergyData = json.data.generationmix
    })
  }
}
</script>

<style>

</style>
