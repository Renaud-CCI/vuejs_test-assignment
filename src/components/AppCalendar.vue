<template>
  <p class="text-2xl font-bold flex justify-start mx-8 mt-6">Ongoing</p>
  <!-- Making one collumn for the hours and another for taskCards-->
  <section id="calendar" ref="calendarSection">
    <div class="grid grid-cols-6">
      <div class="col-span-1">
        <CalendarHours />
      </div>
      <div class="col-span-5">
        <CalendarGrid :selected-day="localSelectedDay"/>
      </div>
    </div>
    </section>
</template>



<script>
import CalendarGrid from './CalendarGrid.vue'
import CalendarHours from './CalendarHours.vue'
import moment from 'moment'
import axios from 'axios'


export default {
  name: 'AppCalendar',
  props: {
    localSelectedDay: {
      type: moment,
      default: null,
    },
  },
  data(){
    return{
      jsonData : null,
    }
  },
  components: {
    CalendarGrid,
    CalendarHours
  }, 
  mounted() {
    this.$refs.calendarSection.scrollTop = 510
    axios
      .get('/api/testAssigmentJson', { proxy: { host: 'https://my-json-server.typicode.com/Renaud-CCI/test-assignment-json', port: 8080 } })
      .then(response => (this.jsonData = response))
  } 
};


</script>

<style scoped>
#calendar{
  height: 50vh;
  overflow-y: auto;
}
#calendar::-webkit-scrollbar { width: 0 !important };
</style>
