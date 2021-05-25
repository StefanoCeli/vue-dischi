<template>
      <div class="col-xs-12 col-sm-5 col-lg-2 mb-3 ms-2 me-2 p-3 p-lg-2 ">
        <a href="#"><img class="img-fluid" :src="card.poster" :alt="card.title"></a>
        <h1 class="text-center  mt-4 mb-4">{{ card.title.toUpperCase() }}</h1>
        <h2 class="text-center">{{ card.author }}</h2>
        <h2 class="text-center">{{ card.year }}</h2>
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
@import '../assets/style/vars.scss';

div{
  background-color: $brand-color;
  img{
    width: 100%;
  }
  h1{
    font-size: 16px;
    font-weight: 600;
    color: #fff;
  }
  h2{
    color: #fff;
    font-size: 14px;
    opacity: .3;
  }
}

</style>