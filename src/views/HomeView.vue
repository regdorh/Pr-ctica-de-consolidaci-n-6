<template>
  <div class="home">
    <h1>Lista de Juegos Disponibles</h1>
    <Juegos></Juegos>
  </div>
</template>

<script>
// @ is an alias to /src
import Juegos from '@/components/Juegos.vue';

export default {
  name: 'HomeView',
  components: {
    Juegos
  }
}
</script>
