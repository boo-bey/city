<template>
  <div class="about">
    <h1>城市选择</h1>
    <van-index-bar :index-list="indexList">
      <div v-for="(item, k) in cityList" :key="k">
        <van-index-anchor :index="k"> {{ k }} </van-index-anchor>
        <van-cell v-for="val in item" :key="val.code" :title="val.city" @click="goHome" />
      </div>



    </van-index-bar>
  </div>
</template> 

<script>

export default {


  data() {
    return {
      // indexList:[1,2,3,4,5]
      cityList: [],
      indexList: []//[A,B,C,D,...]
    }
  },
  created() {
    this.axios.get('data.json').then(res => {
      localStorage.setItem('citylist', res.data)
      let obj = res.data.city_list
      this.cityList = obj
      this.indexList = Object.keys(obj)
    })
  },
  methods:{
    goHome(e){
      let cityName=e.target.innerText;
          localStorage.setItem('city',cityName)
          // this.$router.push('/')
          this.$router.go(-1)
    }
  }
}
</script>
<style scoped>
</style>>

