<template>
  <div>
    <h1>Week 1</h1>
    <DayModule v-for="day in mockData.plan" :key="day" 
      :meals="day.meals">
      <div>
        <div>{{ day.day }}</div>
        <div>Calories: {{day.goal.calories}}</div>
      </div>
    </DayModule>
  </div>
</template>

<script>
import DayModule from "@/components/Module.vue";
import mockData from "@/assets/mockData.json";

export default {
  name: "WeekView",
  components: {
    DayModule
  },
  data: function() {
    return {
      mockData,
    };
  }
};
</script>

<style scoped>

</style>