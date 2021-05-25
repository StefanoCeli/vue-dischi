<template>
      <div class="col d-flex justify-content-center align-items-center flex-column">
        <a href="#"><img class="img-fluid" :src="card.poster" :alt="card.title"></a>
        <h2>{{ card.title.toUpperCase() }}</h2>
      </div>
</template>

<script>
export default {
    name:'Card',
    props: {
        card:Object
    }
}
</script>

<style lang="scss" scoped>
    
div{
  min-width: 250px;
  img{
    height: 100px;
  }
  h2{
    font-size: 12px;
    color: #fff;
  }
}

</style>