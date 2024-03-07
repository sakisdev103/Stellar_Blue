<template>
    <div>
        <!-- Button for selecting date range -->
        <div class="container text-center mb-4">
            <p>Date range</p>
            <div class="input-group">
                <input type="date" class="form-control" v-model="startDate" :max="endDate">
                <div class="input-group-addn">to</div>
                <input type="date" class="form-control" v-model="endDate" :min="startDate">
            </div>
        </div>
        <!-- Passing the filtered data and displaying Data in Table -->
        <Table :filterDates="filterDates"/>
        <!-- Passing the filtered data and displaying Data in Chart -->
        <Chart :filterDates="filterDates"/>
    </div>
    
</template>


<script>
    import Table from './subComponents/Table.vue'
    import Chart from './subComponents/Chart.vue'

    //Importing json file
    import timeseries from '../data/timeseries.json'

    //Getting the date of the first and last item of they array.
    let startDate = timeseries[0].DateTime.slice(0,10);
    let endDate = timeseries[timeseries.length - 1].DateTime.slice(0,10);

    export default{
        name: 'Main',
        components: {
            Table,
            Chart,
        },
        data () {
            return{
                timeseries,
                startDate: startDate,
                endDate: endDate
            }
        },
        computed:{
            //Filtering the json file to take the selected items based on selected date. 
            filterDates(){
                return this.timeseries.filter((date)=>{
                    return date.DateTime.slice(0, 10) >= this.startDate && date.DateTime.slice(0,10) <= this.endDate
                })
            }
        }
    }
    
    
</script>