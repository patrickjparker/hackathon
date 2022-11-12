<template>
  <div class="container">
    {{ msg }}
  </div>
</template>

<script>
export default {
  name: "Module",
  props: {
    msg: String,
  },
};
</script>

<style scoped>
.container {
  border-radius: 50%;
  width: 30px;
  height: 30px;
  border: var(--color-dark) 1px solid;
}
</style>