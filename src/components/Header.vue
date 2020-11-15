<template>
  <b-navbar shadow>
    <template slot="brand"
      ><b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img src="@/assets/logo.png" /> </b-navbar-item
    ></template>
    <template slot="start">
      <b-navbar-item href="#"> Home </b-navbar-item>
      <b-navbar-item href="#">
        <router-link :to="{ path: '/main'}">Main</router-link>
      </b-navbar-item>
      <b-navbar-dropdown hoverable label="Info">
        <b-navbar-item href="#"> About </b-navbar-item>
        <b-navbar-item href="#"> Contact </b-navbar-item>
      </b-navbar-dropdown>
    </template>
    <template slot="end">
      <b-navbar-dropdown hoverable right label="Language">
        <b-navbar-item href="#" value="de"> English </b-navbar-item>
        <b-navbar-item href="#" value="de"> German </b-navbar-item>
      </b-navbar-dropdown>
    </template>
  </b-navbar>
</template>

<script>
export default {
  name: 'Header',
};
</script>
