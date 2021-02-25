<template>
  <div id="app">
    <h1>UK National Energy Usage Sources</h1>
    <date-range :startTime="startTime" :endTime="endTime"></date-range>
    <energy-chart :rawEnergyData="rawEnergyData"></energy-chart>
    <date-range :startTime="startTime" :endTime="endTime"></date-range>
    <energy-bar-chart :rawEnergyData='rawEnergyData'></energy-bar-chart>
    
  </div>
</template>

<script>
import EnergyChart from './components/EnergyChart.vue'
import EnergyBarChart from './components/EnergyBarChart.vue'
import DateTimeRange from './components/DateTimeRange.vue'

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
    'energy-chart': EnergyChart,
    'energy-bar-chart': EnergyBarChart,
    'date-range': DateTimeRange

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
#app{
  font-family: Arial, Helvetica, sans-serif;
  display:flex;
  flex-direction: column;
  align-items: center;
  background-color:goldenrod;
}
h1{
  text-decoration-line: underline;
  font-size:30px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
</style>
