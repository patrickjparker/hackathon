<template>
    <div class="about">
      <h1>Shopping Cart</h1>

        <div v-for="day in mockData.plan" :key="day.day">
            <div class="name">{{ day.day }}</div>
           <div v-for="meal in day.meals" :key="meal.name">
                <div v-for="food in meal.foods" :key="food.id">
                    {{ food.name }}
                </div>
            </div>
            <br>
        </div>
    </div>
  </template>
  
  <script>
  import mockData from "@/assets/mockData.json";

  export default {
    name: "ShoppingCart",
    data: function() {
        return {
            mockData,
        };
    }
    };
  </script>