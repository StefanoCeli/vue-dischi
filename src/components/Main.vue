<template>
  <main>

      <div class="container"
        v-if= "loading === false"
      >
        <h3 class="text-center text-white mb-3">Seleziona per genere</h3>
        <Select />

        <div class="row d-flex justify-content-center">
          <Card
            v-for= "(disco, index) in dischi" :key= "index"
            :card= "disco"
            />
        </div>
      </div>

      <div v-if= "loading" class="loader d-flex justify-content-center align-items-center">
        <div class="lds-facebook"><div></div><div></div><div></div></div>
      </div>

  </main>
</template>

<script>
import axios from 'axios'
import Card from './Card'
import Select from './Select.vue'

export default {
    name:'Main',
    components:{
        Card,
        Select
    },
  data(){
    return {
      axios,
      dischi:[],
      loading:true
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res => {
      this.dischi = res.data.response;
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/utilities.scss';

  main{
    padding: 80px;
    background-color: #1E2D3B;
    height: calc(100vh - 70px);
    overflow-y: auto;
    .loader{
      height: calc(100vh - 230px);
    }
  }
</style>