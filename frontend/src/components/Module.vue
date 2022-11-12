<template>
<div>
  <div :class="['container', (completed ? 'completed' : '')]" @click="$emit('click')">
    <slot/>
  </div>
</div>
</template>

<script>
export default {
  name: "Module",
  props: {
    size: String,
    completed: {
      type: Boolean,
      default: false
    },
    missed: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped>
.container {
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  --size: 100px;
  width: var(--size);
  height: var(--size);
  border: var(--color-dark) 1px solid;
  margin-top: 3em;
  margin-left: auto;
  margin-right: auto;
  clear:both
}

.completed {
  background-color: var(--color-success);
  color: var(--color-white);
}
</style>