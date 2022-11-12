<template>
  <div class="home">
    <WeekView/>
  </div>
</template>

<script>
// @ is an alias to /src
import WeekView from '@/components/WeekView.vue'

export default {
  name: 'Home',
  components: {
    WeekView
  }
}
</script>
