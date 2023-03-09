<template>
<Header/>
<div class="container">
  <router-view/>
</div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  components:{Header}
}
</script>

<style lang="scss" scoped>
.container{
  padding-left: 15px;
  padding-right: 15px;
  margin-left: auto;
  margin-right: auto;
  @media(min-width:768px){
    width: 750px; 
  }
  @media(min-width:992px){
    width: 970px; 
  }
  @media(min-width:1200px){
    width: 1170px; 
  }
}
</style>