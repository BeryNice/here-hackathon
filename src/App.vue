<template>
  <div id="app">
    <div id="nav">
      <router-link to="/home">Home</router-link>
      <router-link to="/login-driver">Eres conductor? Ingresa aquí</router-link>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Map from './components/Map.vue';

export default {
  name: 'app',
  components: {
    Map,
  },
  data() {
    return {
      query: 'schools',
    };
  },
  methods: {
    search() {
      this.$refs.map.places(this.query);
    },
  },
};
</script>

<style>
  @import './css/main.css'
</style>
