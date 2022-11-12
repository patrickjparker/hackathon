<template>
<div>
  <Module @click="show = !show"/>
  <transition>
    <div v-if="show">
      <div v-for="meal in meals" :key="meal.name">
        <div v-for="food in meal.foods" :key="food.id">
          <input type="checkbox" :id="food.name" :value="food.name" v-model="foodsEaten">
          {{ food.name }}
          {{ food.calories }}
        </div>
        <div> Total Calories: {{ meal.totalCalories }} </div>
      </div>
    </div>
  </transition>
</div>
</template>

<script>
import Module from '@componets/Module.vue'
export default {
  name: 'DayModule',
  components: { Module },
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