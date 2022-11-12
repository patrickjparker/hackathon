<template>
<div>
  <Module @click="show = !show" size="110" color="day-color">
    <div>
      <div class="name">{{ day.day }}</div>
      <div>Calories: {{day.goal.calories}}</div>
    </div>
  </Module>
  <transition name="slide-fade">
    <div class="meals" v-if="show">
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
.slide-fade-enter-active, 
.slide-fade-leave-active {
  transition: all 0.2s ease-out;
}

.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}

.name {
  margin: 0.25rem;
  font-size: 1.25rem;
  font-weight: bold;
}  

.meals {
    display: flex;
    justify-content: center;
  }
</style>