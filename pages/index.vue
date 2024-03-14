<script setup lang="ts">

import MatrixDemo from "../component/matrixDemo.vue";
import MatrixPotential from "~/component/matrixPotential.vue";
</script>

<template>
  <div class="container">
    <div class="wrapper">
      <matrix-demo/>
      <matrix-potential/>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  background:linear-gradient(rgba(255,255,255,0.8), rgba(255,255,255,0.8)), url("/img/bg.jpg");
  font-family: Montserrat, sans-serif;
}

.wrapper {
  width: 1140px;
  margin: 0 auto;
}
</style>