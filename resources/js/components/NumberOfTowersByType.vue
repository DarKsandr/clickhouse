<template>
    <div>
        <DoughnutChart :chart-data="data" />
    </div>
</template>
<script setup>
import { DoughnutChart  } from 'vue-chart-3';
import { Chart, registerables } from "chart.js";
import { reactive } from 'vue';
import axios from "axios";
Chart.register(...registerables);

const data = reactive({
    labels: [],
    datasets: [],
});

axios.get(`/api/numberOfTowersByType`).then(res => {
    data.labels = res.data.map(item => item.radio);
    data.datasets = [
        {
            data: res.data.map(item => item.count),
            backgroundColor: ['#77CEFF', '#0079AF', '#123E6B', '#97B0C4', '#A5C8ED'],
        }
    ];
});
</script>