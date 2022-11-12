<template>
<div>
  <Module @click="show = !show" size="75" :completed="allFoodEaten">
    {{ meal.name }}
    {{ meal.totalCalories }}
  </Module>
  <transition>
    <div v-if="show">
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

</style>