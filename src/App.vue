<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';

export default {
  name: 'App',
  components: {
    Header,
  },
};
</script>
<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
