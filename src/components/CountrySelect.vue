<template>
    <select v-model="selected" @change="onChange">
        <option value='0'>Select Country</option>
        <option v-for="country in countries" :key="country.ID" :value="country"> 
        {{country.Country}}</option>
    </select>
</template>

<script>
export default {
    props:['countries'],
    emits:['get-country'],
    data(){
        return{
            selected:0 
        }
    },
    methods:{
        onChange(){
            // const country = this.countries.find((item) => item.ID === this.selected)
            this.$emit('get-country',this.selected)
        }
    }
}
</script>

<style lang="scss">
select{
    padding: 8px 5px;
    margin-top:30px;
    background-color:#eee;
    border: 1px solid #ddd;
    outline: none;
    width: 100%;
}
</style>