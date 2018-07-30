<template>
  <div id="app">
  <nav class="navbar navbar-default">
      <div class="container-fluid">
        <div class="navbar-header">
          <a class="navbar-brand" href="#">Lab SD</a>
        </div>
      </div>
    </nav>
    <BuscaCanciones msg="pasando msg"/>
    <IngresaCanciones msg="pasando msg"/>
  </div>
</template>

<script>
import BuscaCanciones from './components/BuscaCanciones.vue'
import IngresaCanciones from './components/IngresaCanciones.vue'

export default {
  name: 'App',
  components: {
    BuscaCanciones,
    IngresaCanciones
  }
}
</script>

<style>

</style>
