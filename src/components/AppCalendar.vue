<template>
  <p class="text-2xl font-bold flex justify-start mx-8 mt-6">OnGoing</p>
<div class="grid grid-cols-4">
  <div class="col-span-1">
    <CalendarHours />
  </div>
  <div class="col-span-3">
    <CalendarGrid />
  </div>
</div>
</template>



<script>
import CalendarGrid from './CalendarGrid.vue'
import CalendarHours from './CalendarHours.vue'


export default {
  name: 'AppCalendar',
  components: {
    CalendarGrid,
    CalendarHours
  },  
};


</script>

<style scoped>

</style>
