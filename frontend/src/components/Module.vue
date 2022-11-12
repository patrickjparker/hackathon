<template>
<div>
  <div class="container" @click="$emit('click')">
    <slot/>
  </div>
</div>
</template>

<script>
export default {
  name: "Module",
  prop: {
    size: String
  },
  data: function() {
    return {
      complete: false,
      missed: false,
    }
  },
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
  margin-top: 3em;
  margin-left: auto;
  margin-right: auto;
  clear:both
}
</style>