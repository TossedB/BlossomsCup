<template>
    <div class="d-flex">
        <!-- <BarChart :chartData="apm" :options="options" :height="170"/>
        <BarChart :chartData="pps" :options="options" :height="170"/> -->
        <div>
            <div>
                <h4 class="position-relative ms-5">APM</h4>
                <VueApexCharts width="350" type="bar" :options="options" :series="apm"></VueApexCharts>
            </div>
            <div>
                <h4 class="position-relative ms-5">PPS</h4>
                <VueApexCharts width="350" type="bar" :options="options" :series="pps"></VueApexCharts>
            </div>

        </div>

        <div>
            <div>
                <h4 class="position-relative ms-5">APP</h4>
                <VueApexCharts width="350" type="bar" :options="options" :series="app"></VueApexCharts>
            </div>
            <div>
                <h4 class="position-relative ms-5">VS</h4>
                <VueApexCharts width="350" type="bar" :options="options" :series="vs"></VueApexCharts>
            </div>
        </div>
    </div>
</template>

<script setup>
import VueApexCharts from 'vue3-apexcharts'
import { reactive, defineProps } from 'vue';

const p1 = reactive(props.players[0])
const p2 = reactive(props.players[1])

const labels = [p1.name.toUpperCase(), p2.name.toUpperCase()]
const props = defineProps({
  players: Object
})

const options = {
    chart: {
        toolbar: {
            show: false,
        }
    },
    plotOptions: {
        bar: {
            columnWidth: '70%',
            barHeight: '30%',
            horizontal: true
        }
    },
    xaxis: {
        categories: labels,
        labels: {
            offsetY: 10,
            show: true,
            minWidth: 0,
            style: {
                colors: ['#EEEEEE', '#EEEEEE'], // Label colours
                fontSize: '16px',
                fontFamily: 'Helvetica, Arial, sans-serif',
                fontWeight: 700,
            },
        },
        axisBorder: {
            color: '#EEEEEE',
        },
        axisTicks: {
            show: true,
            color: '#EEEEEE',
            height: 10,
            width: 20,
            offsetY: 4
        },
    },
    yaxis: {
        labels: {
            show: true,
            minWidth: 0,
            maxWidth: 160,
            style: {
                colors: ['#C23829', '#BE800E'], // Name colours
                fontSize: '16px',
                fontFamily: 'Helvetica, Arial, sans-serif',
                fontWeight: 700,
            },
        },
        axisBorder: {
            color: '#EEEEEE',
        },
        axisTicks: {
            show: true,
            color: '#EEEEEE',
            width: 5,
        },
    }
}

const apm = [{
    name: 'APM',
    data: [
        {
            x: 'Category A',
            y: p1.apm,
            fillColor: '#C23829',
            strokeColor: '#EEFFFFW'
        }, {
            x: 'Category B',
            y: p2.apm,
            fillColor: '#BE800E',
            strokeColor: '#C23829'
        }
    ]  
}]

const pps = [{
    name: 'PPS',
    data: [
        {
            x: 'Category A',
            y: p1.pps,
            fillColor: '#C23829',
            strokeColor: '#EEFFFFW'
        }, {
            x: 'Category B',
            y: p2.pps,
            fillColor: '#BE800E',
            strokeColor: '#C23829'
        }
    ]  
}]

const app = [{
    name: 'APP',

    data: [
        {
            x: 'Category A',
            y: p1.app.toFixed(2),
            fillColor: '#C23829',
            strokeColor: '#EEFFFFW'
        }, {
            x: 'Category B',
            y: p2.app.toFixed(2),
            fillColor: '#BE800E',
            strokeColor: '#C23829'
        }
    ]  
}]

const vs = [{
    name: 'VS',
    data: [
        {
            x: 'Category A',
            y: p1.vs,
            fillColor: '#C23829',
            strokeColor: '#390040'
        }, {
            x: 'Category B',
            y: p2.vs,
            fillColor: '#BE800E',
            strokeColor: '#C23829'
        }
    ]  
}]
// import { BarChart } from 'vue-chart-3';
// import { Chart, registerables } from "chart.js";
// Chart.register(...registerables);



// const styles = {
//     backgroundColor: [
//         'rgba(255, 99, 132, 0.2)',
//         'rgba(255, 159, 64, 0.2)',
//     ],
//     borderColor: [
//         'rgb(255, 99, 132)',
//         'rgb(255, 159, 64)',
//     ],
//     barThickness: 15,
//     borderWidth: 1
// }

// const apm = {
//     labels: labels,
//     datasets: [
//         {
//             data: [
//                 p1.apm,
//                 p2.apm
//             ],
//             ...styles
//         },
//     ]
// }

// const pps = {
//     labels: labels,
//     datasets: [
//         {
//             label: 'PPS',
//             data: [
//                 p1.pps,
//                 p2.pps
//             ],
//             ...styles
//         },
//     ]
// }

// const options = {
//     indexAxis: 'y',
//     scales: {
//         y: {
//             grid: {
//                 color: 'rgba(255, 99, 132, 0.2)',
//                 borderColor: 'white',
//                 tickColor: 'rgba(255, 99, 132, 0.2)'
//             },
//             ticks: {
//                 color: 'white',
//             }
//         },
//         x: {
//             grid: {
//                 color: 'rgba(255, 99, 132, 0.2)'    ,
//                 borderColor: 'white',
//                 tickColor: 'rgba(255, 99, 132, 0.2)'
//             },
//             ticks: {
//                 color: 'white',
//             }
//         },
//     }
// }
</script>

<style scoped>
h4 {
    font-size: 1.3em;
    font-family: "Now"; 
    color: #FEFADC;
    right: -40px;
    top: 20px;
}
</style>