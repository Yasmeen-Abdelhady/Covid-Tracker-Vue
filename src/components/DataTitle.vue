<template>
    <div class="title">
        <h2>{{title}}</h2>
        <p>{{dataDate}}</p>
        <!-- <p>{{setDate}}</p> -->
    </div>
</template>

<script>
export default {
    props:['title','dataDate'],
}
</script>

<style lang='scss' scoped>
.title{
    text-align: center;
    h2{
        font-size: 27px;
    }
}
</style>