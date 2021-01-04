<template>
  <div class="container center mt-5">
    <div class="row">
      <div class="col-sm border padding ">
        <img :src="getImgUrl('smartphone.png')" width="100" alt="" />
        <h2 class="color-grey">
          <router-link to="/mobile">Mobile</router-link>
        </h2>
      </div>
      <div class="col-sm border padding">
        <img :src="getImgUrl('care.png')" width="100" alt="" />
        <h2 class="color-grey"><a href="">Charity</a></h2>
      </div>
    </div>
    <div class="row ">
      <div class="col-sm border padding">
        <img :src="getImgUrl('water-tap.png')" width="100" alt="" />
        <h2 class="color-grey"><a href="">Communal</a></h2>
      </div>
      <div class="col-sm border padding">
        <img :src="getImgUrl('finance.png')" width="100" alt="" />
        <h2 class="color-grey"><a href="">Finance</a></h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    getImgUrl(pic) {
      return require("../assets/images/" + pic);
    }
  }
};
</script>
