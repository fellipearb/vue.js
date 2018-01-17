<template>
  <main>
    <nav>
      <ul>       
          <li v-for="route in routes">
            <router-link :to="route.path ? route.path : '/'">{{route.titulo}}</router-link>
          </li>
      </ul>
    </nav>
    <router-view></router-view>
  </main>
</template>

<script>
import { routes }  from './routes'

export default {
  data() {
    return {
      routes
    }
  }
}
</script>

<style lang="scss">
  .nav {
    ul {
      li {
        float: left;
      }
    }
  }
</style>