<template>
  <div class="main">
    <div class="loader spinner-border text-primary" role="status"></div>
    <div class="loading">
      <p>Loading....</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "Loader",
};
</script>
<style scoped>
.main {
  height: 750px;
}
.loader {
  position: fixed;
  top: 50%;
  left: 50%;
}
.loading {
  position: fixed;
  top: 55%;
  left: 48%;
  color: #0d6efd;
  font-size: 25px;
  font-weight: 600;
}
</style>
