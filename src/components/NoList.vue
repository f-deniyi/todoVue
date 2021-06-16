<template>
  <div class="nolist">
    <h1>You currently have no todo on your list</h1>
  </div>
</template>
<script>
export default {
  name: "Nolist",
};
</script>

<style scoped>
.nolist {
  text-align: center;
  position:fixed;
  top: 50%;
  left: 30%;
  transform: translate(-50, -50);
}
@media (max-width:600px) {
    .nolist {
  left: 5%;
}
}
</style>