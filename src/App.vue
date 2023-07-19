<template>
  <AppHeader />
  <AppMonthChoice :current-date="currentDate" @month-selected="handleMonthSelected" />
  <MonthDate :selectedMonth="selectedMonth || currentDate" />
  <AppCalendar />
  <div class="endingDiv"></div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMonthChoice from './components/AppMonthChoice.vue'
import MonthDate from './components/MonthDate.vue'
import AppCalendar from './components/AppCalendar.vue'
import moment from 'moment'

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
    };
  },
  methods: {
    handleMonthSelected(month) {
      this.selectedMonth = month;
    },
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