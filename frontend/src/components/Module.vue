<template>
<div>
  <div :style="containerStyle" :class="['container', (completed ? 'completed' : color)]" @click="$emit('click')">
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
    },
    color: {
      type: String,
      default: 'white'
    }
  },
  computed: {
    containerStyle: function() {
      return {
        "--size": this.size + 'px',
      }
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
  width: var(--size);
  height: var(--size);
  border: var(--color-dark) 1px solid;
  background-color: var(--default-background);
  margin-top: 3em;
  margin-left: auto;
  margin-right: auto;
  clear:both
}

.completed {
  background-color: var(--color-success);
  color: var(--color-white);
}

.meal-color {
  background-color: var(--color-meal);
  border: var(--color-meal-border) 1px solid;
}

.day-color {
  background-color: var(--color-day);
}
</style>