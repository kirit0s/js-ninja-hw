<template>
  <div id="app">
    <page-home-work-one/>
  </div>
</template>

<script>
import PageHomeWorkOne from './components/PageHomeWorkOne';

export default {
  name: 'App',
  components: {
    PageHomeWorkOne,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
