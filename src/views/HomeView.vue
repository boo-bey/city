<template>
  <div class="home">
    <div >{{ city}}</div>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {

  },
  data(){
    return{
      city:'shanghai'
    }
  },
  created(){
    let city=localStorage.getItem('city')
    if(city){
      this.city=city
    }
  }
}
</script>
