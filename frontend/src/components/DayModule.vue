<template>
<div>
  <Module @click="show = !show" size="100">
    <div>
      <div class="name">{{ day.day }}</div>
      <div>Calories: {{day.goal.calories}}</div>
    </div>
  </Module>
  <transition>
    <div v-if="show">
      <MealModule v-for="meal in day.meals" :key="meal.id" :meal="meal"/>
    </div>
  </transition>
</div>
</template>

<script>
import Module from '@/components/Module.vue'
import MealModule from './MealModule.vue'
export default {
  name: 'DayModule',
  components: { Module, MealModule },
  props: {
    day: Object
  },
  data: function() {
    return {
      show: false,
      foodsEaten: [],
    }
  },
}
</script>

<style scoped>
.name {
  margin: 0.25rem;
  font-size: 1.25rem;
  font-weight: bold;
}
</style>