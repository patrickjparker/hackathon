<template>
<div class="meal">
  <Module @click="show = !show" size="75" :completed="allFoodEaten">
    <div>
      <div class="name">{{ meal.name }}</div>
      <div>Calories: {{ meal.totalCalories }}</div>
    </div>
  </Module>
  <transition name="slide-fade">
    <div class="food" v-show="show">
      <div v-for="food in meal.foods" :key="food.id">
        <input type="checkbox" :value="food.name" v-model="foodEaten"/>
        <span>{{ food.name }}</span>
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
      foodEaten: [],
    }
  },
  computed: {
    allFoodEaten: function() {
      return this.foodEaten.length === this.meal.foods.length
    }
  },


}
</script>

<style>
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
  font-weight: bold;
}
.meal {
  margin-left: 2em;
  margin-right: 2em;
}

.food {
  margin-top: 1em;
}
</style>