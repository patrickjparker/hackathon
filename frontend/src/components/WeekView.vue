<template>
  <div>
    <h1>Week 1</h1>
    <Module v-for="day in mockData.plan" :key="day">
      <div>
        <div>{{ day.day }}</div>
        <div>Calories: {{day.goal.calories}}</div>
      </div>
    </Module>
  </div>
</template>

<script>
import Module from "@/components/Module.vue";
import mockData from "@/assets/mockData.json";

export default {
  name: "WeekView",
  components: {
    Module
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