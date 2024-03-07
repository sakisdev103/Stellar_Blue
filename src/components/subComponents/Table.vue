<template>
    <div class="table-responsive p-3">
        <table class="table table-light table-hover table-bordered border-dark">
            <thead>
                <tr>
                    <th class="col">DateTime</th>
                    <th class="col">ENTSOE_DE_DAM_Price</th>
                    <th class="col">ENTSOE_GR_DAM_Price</th>
                    <th class="col">ENTSOE_FR_DAM_Price</th>
                </tr>
            </thead>
            <!-- Dynamic display data -->
            <tbody v-for="(item, index) in filterDates" :key="index" >
                <tr>
                    <th>{{ item.DateTime }}</th>
                    <th>{{ item.ENTSOE_DE_DAM_Price }}</th>
                    <th>{{ item.ENTSOE_GR_DAM_Price }}</th>
                    <th>{{ item.ENTSOE_FR_DAM_Price }}</th>
                </tr>

            </tbody>
        </table>
    </div>
</template>


<script>
    export default{
        //Destructuring Prop
        props: ['filterDates'],
        name: 'Table',
        
    }
</script>