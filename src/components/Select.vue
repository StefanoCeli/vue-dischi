<template>

<select 
class="form-select text-white mb-5 ms-auto me-auto"  aria-label="Select genre"
v-model= "selectGenre"
@change= "changeValue"
>
    <option value="" >Tutti</option>
    <option>Pop</option>
    <option>Rock</option>
    <option>Metal</option>
    <option>Jazz</option>
</select>


</template>

<script>
export default {
    name:'Select',
    data(){
        return{
            selectGenre:""
        }
    },
    methods:{
        changeValue(){
            this.$emit('changeGenre',this.selectGenre)
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';

select{
    width: 300px;
    background-color: $brand-color;
}

</style>