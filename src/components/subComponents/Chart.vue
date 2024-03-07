<template>
    <div class="wrapper">
        <canvas id="myChart"></canvas>
    </div>
</template>


<script >
import Chart from 'chart.js/auto';

export default {
    //Destructuring Prop
    props: ['filterDates'],
    name: 'Chart',

    //creating the chart
    mounted(){
        const ctx = document.getElementById('myChart');

        const myChart = new Chart(ctx, {
            type: 'line',
            data: {
            labels: this.filterDates.map((item)=>{return item.DateTime}),
            datasets: [{
                label: 'ENTSOE_DE_DAM_Price',
                data: this.filterDates.map((item)=>{return item.ENTSOE_DE_DAM_Price}),
                borderWidth: 1
            },
            {
                label: 'ENTSOE_GR_DAM_Price',
                data: this.filterDates.map((item)=>{return item.ENTSOE_GR_DAM_Price}),
                borderWidth: 1
            },
            {
                label: 'ENTSOE_FR_DAM_Price',
                data: this.filterDates.map((item)=>{return item.ENTSOE_FR_DAM_Price}),
                borderWidth: 1
            }
            ]
            },
            options: {
            scales: {
                y: {
                beginAtZero: true
                }
            },
            responsive: true,
            maintainAspectRatio: false,
            }
        });
        myChart
        window.chart = myChart
    },
    //Updating the chart based on selected date
    updated() {
        window.chart.data.labels = this.filterDates.map((item)=>{return item.DateTime})
        window.chart.data.datasets[0].data = this.filterDates.map((item)=>{return item.ENTSOE_DE_DAM_Price})
        window.chart.data.datasets[1].data = this.filterDates.map((item)=>{return item.ENTSOE_GR_DAM_Price})
        window.chart.data.datasets[2].data = this.filterDates.map((item)=>{return item.ENTSOE_FR_DAM_Price})
        window.chart.update()
    }

}
</script>