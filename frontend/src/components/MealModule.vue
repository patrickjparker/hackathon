<template>
<div class="meal">
  <Module @click="show = !show" size="75">
    {{ meal.name }}
    {{ meal.totalCalories }}
  </Module>
  <transition>
    <div class="food" v-if="show">
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
.meal {
  margin-left: 2em;
  margin-right: 2em;
}

.food {
  margin-top: 1em;
}
</style>