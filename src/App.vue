<template>
    <div class="jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-sm-6 offset-sm-3">
            <div v-if="alert.message" :class="`alert ${alert.type}`">{{ alert.message }}</div>
            <router-view></router-view>
          </div>
        </div>
      </div>
    </div>
  </template>

  <script>
  import { mapState, mapActions } from 'vuex';

  export default {
    name: 'App',
    computed: {
      ...mapState('alert', ['alert']),
    },
    methods: {
      ...mapActions('alert', ['clear']),
    },
    watch: {
      $route(to, from) {
        // clear alert on location change
        this.clear();
      },
    },
  };
  </script>
