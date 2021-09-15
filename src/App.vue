<template>
  <div id="app" class="h-100">
    <div class="container-fluid h-100">
      <div class="row h-100">
        <div
          class="
            col-md-3
            logo-bg
            h-100
            d-flex
            justify-content-center
            align-items-center
          "
        >
          <img alt="Vue logo" src="./assets/aturtoko_logo.png" width="100" />
        </div>
        <div
          class="
            col-md-9
            h-100
            d-flex
            justify-content-center
            align-items-center
          "
        >
          <div class="col-md-8 text rounded px-5 py-4 shadow bg-white">
            <AturToko />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AturToko from "./components/AturToko.vue";

export default {
  name: "App",
  components: {
    AturToko,
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
.logo-bg {
  background: #bce5d0;
}
.text {
  text-align: left;
}
</style>
