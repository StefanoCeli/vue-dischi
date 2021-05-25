<template>
  <main>
      <div class="container">
        <div class="row ">
          <Card
            v-for="(disco, index) in dischi" :key="index"
            :card="disco"
            />
        </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios'
import Card from './Card'

export default {
    name:'Main',
    components:{
        Card
    },
  data(){
    return {
      axios,
      dischi:[]
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res => {
      this.dischi = res.data.response
    })
    .catch(err =>{
      console.log(err);
    })
  }
}
</script>

<style lang="scss" scoped>
  main{
    padding: 50px;
    background-color: #1E2D3B;
    height: calc(100vh - 70px);
  }
</style>