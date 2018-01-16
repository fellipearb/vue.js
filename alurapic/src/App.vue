<template>
  <div class="slider">
    <h1 class="titulo">{{ titulo }}</h1>
    <div class="filtro">
      <input type="search" class="input-filtro" @input="filtro = $event.target.value" placeholder="o que você procura?">
    </div>
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of filtrarFotos">
        <meu-painel :titulo="foto.titulo">
          <img slot="imagem" class="img-responsive" :src="foto.url" :alt="foto.titulo">
        </meu-painel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from './components/shared/painel/Painel.vue'

export default {
  components: {
    'meu-painel' : Painel
  },
  data() {
    return {
      titulo: 'Opalas & Caravans',
      fotos: [],
      filtro: ''
    }
  },
  computed: {
    filtrarFotos() {
      if(this.filtro) {
        let filter = new RegExp(this.filtro.trim(), 'i')
        return this.fotos.filter(foto => filter.test(foto.titulo))
      } else {
        return this.fotos
      }
    }
  },
  created() {
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos)
  }
}
</script>

<style lang="scss">
  .slider {
    max-width: 96%;
    margin: 0 auto;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

    .titulo {
      text-align: center;
    }

    .lista-fotos {
      list-style: none;
      padding: 0;

      .lista-fotos-item {
        width: 15%;
        float: left;
      }
    }

    .filtro {
      padding: 0 20px;
    }

    .input-filtro {
      width: 100%;
      max-width: 500px;
      height: 40px;
      border-radius: 5px;
      border: 1px solid #d3d3d3;
      padding: 0 10px;
    }
  }

  .img-responsive {
    max-width: 100%;
  }
</style>
