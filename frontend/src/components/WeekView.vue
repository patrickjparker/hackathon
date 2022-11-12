<template>
  <div>
    <h1>Week 1</h1>
    <DayModule v-for="day in mockData.plan" :key="day.day" :day="day">
    </DayModule>
  </div>
</template>

<script>
import DayModule from "@/components/DayModule.vue";
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
h1 {
  margin: 0.25rem;
}
</style>