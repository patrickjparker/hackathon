<template>
<div>
  <Module @click="show = !show" size="75">
    {{ meal.name }}
    {{ meal.totalCalories }}
  </Module>
  <transition>
    <div v-if="show">
      <div v-for="food in meal.foods" :key="food.id">
        {{ food.name }}
      </div>
      <div>Total Calories: {{ meal.totalCalories }}</div>
    </div>
  </transition>

</div>
</template>

<script>
import Module from '@/components/Module.vue'
export default {
  components: { Module },
  props: {
    meal: Object
  },
  data: function() {
    return {
      show: false,
    }
  }

}
</script>

<style>

</style>