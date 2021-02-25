<template>
    <div id="bar-chart">
            <GChart
            type="BarChart"
            :data="chartData"
            :options="chartOptions"
        />
        
    </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
    name: 'energy-bar-chart',
    props: ['rawEnergyData'],
    data() {

        return {
            chartOptions: {
                title: "Energy Usage Bar Chart",
                width: 800,
                height: 800,
               
                }
            }
    },
    components: {
        GChart
    },
    computed: {
        chartData: function() {
            if (this.rawEnergyData) { 
                const data = this.rawEnergyData.map(entry => Object.values(entry))
                data.unshift(Object.keys(this.rawEnergyData[0]))
                return data
            } 
            return null
        }
    },
}

</script>

<style>
#bar-chart{
    border:4px inset black;
}

</style>