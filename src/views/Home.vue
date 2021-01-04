<template>
  <div class="home">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Services />
  </div>
</template>

<script>
// @ is an alias to /src
import Services from "@/components/Services.vue";

export default {
  name: "Home",
  components: {
    Services
  },
  methods: {
    getImgUrl(pic) {
      return require("../assets/" + pic);
    }
  }
};
</script>
