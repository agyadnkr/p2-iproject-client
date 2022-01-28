<template>
  <div>
    <button
      @click="goToDetail(location.id)"
      class="w-full h-48 border flex flex-col hover:bg-blue-200"
    >
      <div
        class="h-1/2 text-2xl text-left px-8 pt-6"
        style="font-family: 'Encode Sans', sans-serif; font-weight: 700"
      >
        {{ location.name }}
      </div>
      <div
        class="text-xl text-left mt-6 px-8"
        style="font-family: 'Encode Sans', sans-serif; font-weight: 400"
      >
        {{ location.address }}
      </div>
      <div
        class="text-xl text-left px-8 pb-6 pt-2"
        style="font-family: 'Encode Sans', sans-serif; font-weight: 400"
      >
        {{ currencyProcess(location.price) }}
      </div>
    </button>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "Card",
  props: ["location"],
  methods: {
    ...mapActions(["detailHandler"]),
    goToDetail(locationId) {
      // router.push({
      //   name: "LocationDetail",
      //   params: { locationId: this.location.id },
      // });
      this.detailHandler(locationId);
    },
    currencyProcess(data) {

      return new Intl.NumberFormat("id-ID", {
        style: "currency",
        currency: "IDR",
      }).format(data);
    },
  },
};
</script>

<style>
</style>