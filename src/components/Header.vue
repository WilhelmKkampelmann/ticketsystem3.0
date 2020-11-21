<template>
  <b-navbar shadow centered>
    <template slot="brand"
      ><b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img src="@/assets/logo.png" /> </b-navbar-item
    ></template>
    <template slot="start" >
      <b-navbar-item href="#">
        <router-link :to="{ path: '/'}">Home</router-link>
      </b-navbar-item>
      <b-navbar-item href="#">
        <router-link :to="{ path: '/main'}">Customer Service</router-link>
      </b-navbar-item>
      <b-navbar-dropdown hoverable label="Info">
        <b-navbar-item href="#">
          <router-link :to="{ path: '/about'}">About</router-link>
        </b-navbar-item>
        <b-navbar-item href="#">
          <router-link :to="{ path: '/contact'}">Contact</router-link>
        </b-navbar-item>
      </b-navbar-dropdown>
    </template>
    <template slot="end">
      <b-field>
      <b-select v-model="lang" @input="f($event)">
        <option value="de">
          deutsch
        </option>
        <option value="en">
          english
        </option>
      </b-select>
    </b-field>
    </template>
  </b-navbar>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      lang: localStorage.getItem('lang' || 'en'),
    };
  },
  methods: {
    f(event) {
      localStorage.setItem('lang', event);
      this.$i18n.locale = localStorage.getItem('lang');
    },
  },
};
</script>

<style scoped>
*{
  text-decoration: none;
}
</style>
