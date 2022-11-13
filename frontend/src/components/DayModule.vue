<template>
<div>
  <Module @click="toggle" size="130" color="day-color" :completed="allMealsComplete">
    <div>
      <div class="name">{{ day.day }}</div>
      <div>Calories: <template v-if="!edit">{{day.goal.calories}}</template>
        <template v-else>
          <input type="number" class="input-num" v-model="numToEdit" @input="updateGoal"/>
          <button @click.stop="saveNewValue()">Save</button>
        </template>
          <svg v-if="!show && !edit" style="margin:.1rem" class="icon" @click="editMode()" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--! Font Awesome Pro 6.2.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M421.7 220.3l-11.3 11.3-22.6 22.6-205 205c-6.6 6.6-14.8 11.5-23.8 14.1L30.8 511c-8.4 2.5-17.5 .2-23.7-6.1S-1.5 489.7 1 481.2L38.7 353.1c2.6-9 7.5-17.2 14.1-23.8l205-205 22.6-22.6 11.3-11.3 33.9 33.9 62.1 62.1 33.9 33.9zM96 353.9l-9.3 9.3c-.9 .9-1.6 2.1-2 3.4l-25.3 86 86-25.3c1.3-.4 2.5-1.1 3.4-2l9.3-9.3H112c-8.8 0-16-7.2-16-16V353.9zM453.3 19.3l39.4 39.4c25 25 25 65.5 0 90.5l-14.5 14.5-22.6 22.6-11.3 11.3-33.9-33.9-62.1-62.1L314.3 67.7l11.3-11.3 22.6-22.6 14.5-14.5c25-25 65.5-25 90.5 0z"/></svg>
      </div>
    </div>
  </Module>
  <transition name="slide-fade">
    <div class="meals" v-if="show">
      <MealModule v-for="meal in day.meals" :key="meal.name" 
        :dayTotal="day.goal.calories"
        :meal="meal" @input="complete => handleComplete(meal.name, complete)"/>
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
      daysComplete: [],
      edit: false,
      numToEdit: 0
    }
  },
  methods: {
    handleComplete: function(id, complete) {
      if (complete) {
        this.daysComplete.push(id)
      } else {
        this.daysComplete = this.daysComplete.filter(mealId => mealId !== id)
      }
    },
    editMode: function() {
      this.numToEdit = this.day.goal.calories
      this.edit = true;
    },
    saveNewValue: function() {
      this.edit = false;
      let newNum = parseInt(this.numToEdit)
      this.$emit('input', newNum)
    },
    toggle: function() {
      if (!this.edit) {
        this.show = !this.show
      }
    },
  },
  computed: {
    allMealsComplete: function() {
      return this.daysComplete.length === this.day.meals.length
    }
  }
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

.icon {
  width: .75rem;
  height: .75rem;
  display: inline;
}

.input-num {
  width: 3rem;
  text-align: center;
  margin-bottom: .2rem;
}
</style>