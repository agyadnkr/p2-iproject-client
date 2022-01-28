<template>
  <div id="nav">
    <div class="w-screen h-24 bg-white flex justify-around">
      <div class="w-1/3 h-full flex items-center ml-12">
        <router-link
          class="text-2xl text-slate-100"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
          to="/"
          >Where's the Toilet?</router-link
        >
      </div>
      <div class="w-1/3 h-full flex items-center ml-12 ml-12">
        <router-link
          class="text-2xl text-slate-100"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
          to="/location/add"
          >Add Location</router-link
        >
      </div>
      <div class="w-1/3 h-full flex justify-end items-center mr-12 gap-x-5">
        <router-link
          v-if="isLogged"
          class="text-2xl text-slate-100"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
          to="/favourite"
          >My Favourite</router-link
        >
        <router-link
        v-if="!isLogged"
          class="text-2xl text-slate-100"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
          to="/login"
          >Login</router-link
        >
        <button
        v-if="isLogged"
          class="text-2xl text-slate-100 hover:bg-red-500"
          style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
          to="/login"
          @click="logoutHandler"
        >
          Logout
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapMutations, mapState } from "vuex";
import Swal from "sweetalert2";

export default {
  name: "Navbar",
  computed: {
    ...mapState(["isLogged"]),
  },
  methods: {
    ...mapMutations(["SET_ISLOGGED"]),
    logoutHandler() {
      localStorage.clear();
      this.SET_ISLOGGED(false);
      this.$router.push("/");
      Swal.fire({
        icon: "success",
        title: "Yeayy..",
        text: "Logout Success",
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 0px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>