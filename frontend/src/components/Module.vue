<template>
<div>
  <div class="container">
    <slot/>
  </div>
</div>
</template>

<script>
export default {
  name: "Module",
};
</script>

<style scoped>
.container {
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  --size: 100px;
  width: var(--size);
  height: var(--size);
  border: var(--color-dark) 1px solid;
  margin-bottom: 2em;
  margin-left: auto;
  margin-right: auto;
}
</style>