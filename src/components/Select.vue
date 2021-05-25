<template>

<select class="form-select text-white mb-5 ms-auto me-auto"  aria-label="Select genre">
    <option value="">Tutti</option>
    <option value="Pop">Pop</option>
    <option value="Rock">Rock</option>
    <option value="Metal">Metal</option>
    <option value="Jazz">Jazz</option>
</select>

</template>

<script>
export default {
    name:'Select'
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';

select{
    width: 300px;
    background-color: $brand-color;
}

</style>