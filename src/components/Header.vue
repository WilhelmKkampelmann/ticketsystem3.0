<template>
<section>
  <b-navbar shadow centered>
    <template slot="brand"
      ><b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img src="@/assets/logo.png" /> </b-navbar-item
    ></template>
    <template slot="start" >
      <b-navbar-item href="#">
        <router-link :to="{ path: '/'}">{{$t('nav.home')}}</router-link>
      </b-navbar-item>
      <b-navbar-item href="#">
        <router-link :to="{ path: '/main'}">{{$t('nav.customer-service')}}</router-link>
      </b-navbar-item>
      <b-navbar-dropdown hoverable label="Info">
        <b-navbar-item href="#">
          <router-link :to="{ path: '/about'}">{{$t('nav.about')}}</router-link>
        </b-navbar-item>
        <b-navbar-item href="#">
          <router-link :to="{ path: '/contact'}">{{$t('nav.contact')}}</router-link>
        </b-navbar-item>
      </b-navbar-dropdown>
    </template>
    <template slot="end">
      <b-field>
      <b-select v-model="lang" @input="f($event)">
        <option value="en">
          English
        </option>
        <option value="de">
          Deutsch
        </option>
      </b-select>
    </b-field>
    </template>
  </b-navbar>
</section>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      lang: 'en' || localStorage.getItem('lang'),
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
