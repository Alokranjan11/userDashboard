<template>
  <div class="alert">
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: "Alert",
};
</script>
<style scoped>
.alert {
  width: 30%;
  background: #ffff;
  height: 320px;
  position: fixed;
  top: 30%;
  left: 33%;
  border: 1px solid rgba(0, 0, 10, 0.2);
  box-shadow: 2px 2px 5px 4px rgba(0, 0, 0, 0.1);
  /* transition: all 10s ease-in-out 10s; */
  animation-name:alertBox ;
  animation-duration: 0.3s;
  animation-iteration-count: 1;
  /* animation-delay: 0.5s; */
}
@keyframes alertBox{
    from{
        width: 0%;
        height: 0px;
    }
    to{
        width: 30%;
        height: 320px;
    }
}
</style>
