<template>
    <div class="data-boxes">
        <div class="box cases">
            <h3>Cases</h3>
            <div class="new"> <span>New:</span>
                {{numberWithCommas(stats.NewConfirmed)}}                         
            </div>
            <div> <span>Total:</span> {{numberWithCommas(stats.TotalConfirmed)}} </div>
        </div>

        <div class="box deaths">
            <h3>Deaths</h3>
            <div class="new"> <span>New:</span> 
                {{numberWithCommas(stats.NewDeaths)}}
            </div>
            <div> <span>Total:</span> {{numberWithCommas(stats.TotalDeaths)}}</div>
        </div>
    </div>
</template>

<script>
export default {
    props:['stats'],
    methods: {
        numberWithCommas(x){
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    }
}
</script>

<style lang="scss" scoped>
.data-boxes{
    display: grid;
    grid-template-columns: repeat(auto-fill , minmax(400px,1fr));
    gap: 30px;
    margin-top: 40px;
    .box{
        text-align: center;
        padding-top: 10px;
        padding-bottom: 20px;
        border-radius: 3px;
        &.cases{
            background-color: #b8e2f2;
        }
        &.deaths{
            background-color: #9dd9f3;
        }
        h3{
            color: navy;
            font-weight: bold;
            font-size: 22px;
        }
        .new{
            margin-bottom: 20px;
        }
        span{
            font-weight: bold;
        }
    }
}
</style>