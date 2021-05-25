<template>
  <main>

      <div class="container"
        v-if= "loading === false"
      >

      <h3 class=" text-white text-center mb-4">Seleziona un genere</h3>
      <!-- richiamo all'interno di select l'evento custom 'changeGenre' e avvio la funzione 'catchGenre' -->
        <Select
          @changeGenre= "catchGenre" 
         />

        <div class="row d-flex justify-content-center">
          <Card
            v-for= "(disco, index) in filterGenre" :key= "index"
            :card= "disco"
            />
        </div>
      </div>

      <!-- LOADER -->
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
      loading:true,
      musicGenre:""
    }
  },
  created(){
    //richiamo i dati tramite l'API
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res => {
      this.dischi = res.data.response;
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },
  methods:{
    //funzione che ha come parametro la stringa passata dal componente select tramite $emit 
    catchGenre(text){
      this.musicGenre = text
    }
  },
  computed:{
    //tramite computed la funzione rimane in ascolto e si avvierà soltanto se noterà che un parametro è stato cambiato,facendo cosi la cpu sforza di meno 
    filterGenre(){

      if(this.musicGenre === ""){
        return this.dischi
      }
      return this.dischi.filter(item => item.genre === this.musicGenre)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/utilities.scss';

  main{
    padding: 30px;
    background-color: #1E2D3B;
    height: calc(100vh - 70px);
    overflow-y: auto;
    .loader{
      height: calc(100vh - 130px);
    }
  }
</style>