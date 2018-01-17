<template>
  <div class="painel">
    <button class="painel-titulo" @click="showImage = !showImage">{{ titulo }}</button>
    <transition name="painel-fade">
      <div class="painel-conteudo" v-show="showImage">
        <slot name="imagem"></slot>
        <slot name="btn"></slot>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: ['titulo'],
  data() {
    return {
      showImage : true
    }
  }
}
</script>

<style lang="scss" scoped>
  .painel {
    padding: 20px;
  }

  .painel-titulo {
    width: 100%;
    text-align: center;
    font-size: 14px;
    background: blueviolet;
    color: #fff;
    display: block;
    margin: 0;
    padding: 15px;
    border: none;
  }

  .painel-fade-enter, .painel-fade-leave-active {
    opacity: 0;
  }

  .painel-fade-leave-active, .painel-fade-enter-active {
    transition: opacity .2s;
  }
</style>
