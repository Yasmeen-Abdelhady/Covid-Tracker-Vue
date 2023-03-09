<template>
    <section v-if="!loading"> 
        <DataTitle :title="title" :dataDate="dataDate"/>
        <DataBoxes :stats="stats"/>
        <CountrySelect :countries="countries" @get-country="getCountry"/>
        <button class="clear" @click="clearCountryData">Clear Country</button>
    </section>



    <section v-else class="loading">
        <Loader/> 
        <p>Data is Loading</p>
    </section>
</template>

<script>
import DataTitle from '../components/DataTitle.vue'
import DataBoxes from '../components/DataBoxes.vue'
import CountrySelect from '../components/CountrySelect.vue'
import Loader from '../components/Loader.vue'

export default {
    components :{DataTitle , DataBoxes , CountrySelect , Loader},
    data(){
        return{
            loading: true,
            title:'Global',
            dataDate:'',
            stats: {},
            countries: []
        }
    },
    methods:{
        async fetchData(){
        const res = await fetch('https://api.covid19api.com/summary')
        const data = await res.json()
        return data
        },
        getCountry(country){
            this.stats = country
            this.title = country.Country
        },
        async clearCountryData(){
            this.loading = true
            const data = await this.fetchData()
            this.stats = data.Global
            this.title = 'Global'
            this.loading = false
        }
    },
    async created() {
        const data = await this.fetchData()
        this.dataDate = data.Date
        this.stats = data.Global
        this.countries = data.Countries
        this.loading = false
    }
}
</script>

<style lang="scss">
.loading{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-top: 100px;
    padding-bottom: 100px;
}
.clear{
    background-color:#3f51b5;
    color: white;
    padding: 10px 15px;
    border: 0;
    outline: none;
    display: block;
    margin-top: 30px;
    margin-bottom: 20px;
    cursor: pointer;
}
</style>