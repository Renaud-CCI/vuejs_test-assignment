<template>
  <AppHeader :jsonData="jsonData"/>
  <AppMonthChoice :current-date="currentDate" @month-selected="handleMonthSelected" :local-selected-day="localSelectedDay" />
  <MonthDate :selectedMonth="selectedMonth || currentDate" :local-selected-day="localSelectedDay" @local-selected-day-changed="updateLocalSelectedDay" />
  <AppCalendar :local-selected-day="localSelectedDay || currentDate"/>
  <!-- Add a div to have a backgroud until the end of the screen-->
  <div class="endingDiv"></div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMonthChoice from './components/AppMonthChoice.vue'
import MonthDate from './components/MonthDate.vue'
import AppCalendar from './components/AppCalendar.vue'
import moment from 'moment'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    AppHeader,
    AppMonthChoice,
    MonthDate,
    AppCalendar,
  },
  data() {
    return {
      selectedMonth: null,
      currentDate: moment("2022-02-12"),
      localSelectedDay:null,
      jsonData: {},
    };
  },
  methods: {
    handleMonthSelected(month) {
      this.selectedMonth = month;
    },
    updateLocalSelectedDay(day) {
      this.localSelectedDay = day;
    },
  },
  mounted() {
    //call the API
    axios
      .get('https://my-json-server.typicode.com/Renaud-CCI/testAssigmentJson/data')
      .then(response => (this.jsonData=response.data));
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #DBE9F6;
}

.endingDiv{
  position: fixed;
  z-index: -10;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100vh;
  background-color: #DBE9F6;
  overflow-y: hidden;
}
</style>