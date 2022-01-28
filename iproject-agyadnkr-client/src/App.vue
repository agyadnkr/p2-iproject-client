<template>
  <div id="app">
    <navbar />
    <router-view />
  </div>
</template>

<script>

import Navbar from './components/Navbar.vue'
import { mapMutations } from 'vuex'

export default {
  components: { Navbar },
  name: 'App',
  component: {
    Navbar
  },
  computed: {
    ...mapMutations(['SET_ISLOGGED'])
  },
  created() {
    if(localStorage.getItem('access_token')) {
      this.$store.commit('SET_ISLOGGED', true)
    }
  }
}
</script>
