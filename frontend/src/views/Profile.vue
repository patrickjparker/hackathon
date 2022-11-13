<template>
  <div class="about">
    <h1>Register</h1>
    <div class="container">
    <form onSubmit="return false" class="grid">
      <label for="name">Name: </label>
      <input type="text" id="name">
      <label for="age">Age: </label>
      <input type="text" id="age">
      <label for="sex">Sex: </label>
      <input type="text" id="sex">
      <label for="current">Current Weight: </label>
      <input type="text" id="current">
      <label for="goal">Goal Weight: </label>
      <input type="text" id="goal">
      <div></div>
      <input type="submit" value="Submit" @click="submit">
    </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
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
  width: 40%;
  grid-template-columns: 1fr 1fr;
  grid-gap: .25rem;
  justify-content: center;
  align-items: center;
}
</style>