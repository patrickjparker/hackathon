<template>
  <div class="about">
    <h1>Create New NutriPlan</h1>
    <div class="container">
    <form onSubmit="return false" class="grid">
      <label for="name">Plan Name: </label>
      <input type="text" id="name">
      <label for="current">Current Weight: </label>
      <input type="text" id="current">
      <label for="goal">Goal Weight: </label>
      <input type="text" id="goal">
      
      <label for="goal-choice">Plan Focus:</label>
      <input list="goal-options" id="goal-choice" name="goal-choice" />
      <datalist id="goal-options">
          <option v-for="option in options" :key="option">{{option}}</option>
      </datalist>

      <label id="food-pref-title">Food Preferences:</label>

      <div class="container">
        <input type="radio" id="white-rice" name="rice" value="white rice">
        <label for="white-rice">White Rice</label>
        <input type="radio" id="brown-rice" name="rice" value="brown rice">
        <label for="brown-rice">Brown Rice</label>
      </div>
      <br>
      <div class="container">
        <input type="radio" id="steak" name="meat" value="steak">
        <label for="steak">Steak</label>
        <input type="radio" id="chicken" name="meat" value="chicken">
        <label for="chicken">Chicken</label>
      </div>

      <div></div>
      <input type="submit" value="Create Plan" @click="submit">
    </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  data() {
        return {
            options: [
                'Calories',
                'Protein',
                'Carbs',
                'Weight',
            ]
        }
    },
  methods: {
    submit: function() {
      this.$emit('submit');
    }
  }
}
</script>

<style scoped>
input {
  margin: .5rem;
  border-radius: 5px;
}

label {
  justify-self: end;
}

.container {
  display: flex;
  justify-content: center;
}

.grid {
  display: grid;
  width: 25%;
  grid-template-columns: auto 1fr;
  grid-gap: .25rem;
  justify-content: center;
  align-items: center;
}

</style>