<template>
    <div id="pie-chart">
        <GChart
            type="PieChart"
            :data="chartData"
            :options="chartOptions"
        />
        
    </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
    name: 'energy-chart',
    props: ['rawEnergyData'],
    data() {

        return {
            chartOptions: {
                title: "Energy Usage Pie Chart",
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
                console.log(`${data}`);
                data.unshift(Object.keys(this.rawEnergyData[0]))
                console.log(data);
                return data
            } 
            return null
        }
    },
}

</script>

<style>
#pie-chart{
    border:4px inset black;
}
</style>