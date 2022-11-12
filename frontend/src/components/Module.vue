<template>
<div>
  <div class="container" @click="show = !show">
    <slot/>
  </div>
  <transition>
    <div v-if="show">
      <div v-for="meal in mockData.plan" :key="meal.id">
        <div v-for="food in meal.foods" :key="food.id">
          <input type="checkbox" :id="food.id" :value="food.id" v-model="foodsEaten">
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
export default {
  name: "Module",
  props: {
    day: String,
    meals: Array
  },
  data: function() {
    return {
      show: false,
      foodsEaten: []
    };
  }
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
}
</style>