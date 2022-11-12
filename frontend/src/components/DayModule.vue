<template>
<div>
  <Module @click="show = !show" size="100">
    <slot/>
  </Module>
  <transition>
    <div v-if="show">
      <MealModule v-for="meal in meals" :key="meal.id" :meal="meal"/>
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
    meals: Array
  },
  data: function() {
    return {
      show: false,
      foodsEaten: [],
    }
  },
}
</script>

<style>

</style>