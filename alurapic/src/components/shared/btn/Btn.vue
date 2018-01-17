<template>
  <button :type="tipo" class="btn-default btn-red">{{ texto }}</button>
</template>

<script>
export default {
    props: ['tipo', 'texto']
}
</script>

<style lang="scss" scoped>
    .btn-default {
        border: none;
        display: block;
        margin: 0 auto;
        width: 100%;
        height: 40px;
        font-size: 18px;

        &.btn-red {
            background: red;
            color: #fff;
        }
    }
</style>
