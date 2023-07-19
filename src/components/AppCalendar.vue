<template>
  <p class="text-2xl font-bold flex justify-start mx-8 mt-6">OnGoing</p>
  <section id="calendar" ref="calendarSection">
    <div class="grid grid-cols-4">
      <div class="col-span-1">
        <CalendarHours />
      </div>
      <div class="col-span-3">
        <CalendarGrid :selected-day="localSelectedDay"/>
      </div>
    </div>
    </section>
</template>



<script>
import CalendarGrid from './CalendarGrid.vue'
import CalendarHours from './CalendarHours.vue'
import moment from 'moment'


export default {
  name: 'AppCalendar',
  props: {
    localSelectedDay: {
      type: moment, // Assurez-vous d'importer moment dans le composant
      default: null,
    },
  },
  components: {
    CalendarGrid,
    CalendarHours
  }, 
   mounted() {
    this.$refs.calendarSection.scrollTop = 550;
  } 
};


</script>

<style scoped>
#calendar{
  height: 50vh;
  overflow-y: auto;
}
</style>
