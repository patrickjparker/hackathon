<template>
<div class="meal">
  <Module @click="show = !show" size="105" :completed="allFoodEaten" color="meal-color">
    <div>
      <div class="name">{{ meal.name }}</div>
      <div>Calories: {{ meal.totalCalories }}</div>
    </div>
  </Module>
  <transition name="slide-fade">
    <div class="food" v-show="show">
      <div class="grid">
        <template v-for="food in foodsWithCheckboxes">
          <input type="checkbox" :value="food.checked" :key="food.id" 
            :id="food.name" @input="handleCheckbox($event.target.id)"/>
          <span :key="food.id">{{ food.name }}</span>
        </template>
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
    },
    foodsWithCheckboxes: function() {
      return this.meal.foods.map(food => {
        return {
          ...food,
          checked: false
        }
      })
    }
  },
  methods: {
    handleCheckbox: function(id) {
      if (this.foodEaten.includes(id)) {
        this.foodEaten = this.foodEaten.filter(food => food !== id)
      } else {
        this.foodEaten.push(id)
      }
    }
  }

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

.grid {
  display: grid;
  grid-template-columns: auto 1fr;
  column-gap: .2rem;
}
</style>