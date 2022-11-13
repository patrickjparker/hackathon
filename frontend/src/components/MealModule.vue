<template>
<div class="meal">
  <Module @click="show = !show" size="105" :completed="allFoodEaten" color="meal-color">
    <div>
      <div class="name">{{ meal.name }}</div>
      <div>Calories: {{ meal.percent * dayTotal }}</div>
    </div>
  </Module>
  <transition name="slide-fade">
    <div class="food" v-show="show">
      <div class="grid">
        <template v-for="food in mealCheckbox">
          <input type="checkbox" :value="food.checked" :key="food.id" 
            :id="food.name" @input="handleCheckbox($event.target.id)"/>
          <span @click="handleCheckbox(food.name)" :key="food.id">{{ food.name }}</span>
        </template>
      </div>
    </div>
  </transition>
</div>
</template>

<script>
import Module from '@/components/Module.vue'
export default {
  components: { Module },
  props: {
    meal: Object,
    dayTotal: Number
  },
  data: function() {
    return {
      show: false,
      mealCheckbox: [],
    }
  },
  computed: {
    allFoodEaten: function() {
      return this.mealCheckbox.every(food => food.checked)
    }
  },
  methods: {
    handleCheckbox: function(id) {
      const food = this.mealCheckbox.find(food => food.name === id)
      food.checked = !food.checked
      this.$emit('input', this.mealCheckbox.every(food => food.checked))
    }
  },
  created: function() {
    let total = 0;
    this.mealCheckbox = this.meal.foods.reduce((prev, food) => {
      console.log(this.meal.percent * this.dayTotal)
      if (total < (this.meal.percent * this.dayTotal)) {
        total += food.calories
        prev.push({ ...food, checked: false })
      }
      return prev
    }, [])
    
    
    // this.meal.percent * this.dayTotal
    // this.mealCheckbox = this.meal.foods.map(food => {
    //   return {
    //     ...food,
    //     checked: false
    //   }
    // })
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