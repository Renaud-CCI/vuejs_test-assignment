<template>
<div class="grid grid-cols-6 gap-3 items-center">
    <!-- Create 4 divs for 4 days withe an arrow at the beginning and the end to change days if clicked and a function on days cards to change the selected day variable-->
    <div class="flex justify-end">
      <font-awesome-icon :icon="arrowLeftIcon" class="cursor-pointer" @click="goToPreviousDay"/>
    </div>

    <div v-for="day in days" :key="day" 
    :class="[
      'cursor-pointer border hover:border-purple-800 rounded-full h-20 w-14 sm:h-40 sm:w-32 mx-auto flex flex-col justify-center items-center',
      { 'bg-purple-800 text-white': day.isSame(localSelectedDay, 'day') },
      { 'bg-white text-purple-800': !day.isSame(localSelectedDay, 'day') },
    ]"    
    @click="changeLocalSelectedDay(day)">

      <p class="text-xl font-bold">{{ day.format('D') }}</p>
      <p>{{ day.format('ddd') }}</p>

    </div>
    <div class="flex justify-start">
      <font-awesome-icon :icon="arrowRightIcon" class="cursor-pointer" @click="goToNextDay"/>
    </div>
</div>
</template>



<script>
import { faArrowLeft, faArrowRight } from '@fortawesome/free-solid-svg-icons';
import moment from 'moment'


export default {
  name: 'MonthDate',
  props: {
    selectedMonth: {
      type: moment,
      default: null,
    },
    currentDate: {
      type: moment,
      default: null,
    },
  },
  data() {
    return {
      arrowLeftIcon: faArrowLeft,
      arrowRightIcon: faArrowRight,
      localSelectedMonth: null,
      localSelectedDay:null,
    };
  },
  computed: {
    days() {
      // Calculating the day to display in relation to the selected month
      const startDate = this.localSelectedMonth ? moment(this.localSelectedMonth) : this.selectedMonth ? moment(this.selectedMonth) : moment(this.currentDate);
      // initiate a date array for days to display
      const days = [startDate.clone()];

      // Générate the 3 other days for the array
      for (let i = 1; i < 4; i++) {
        const nextDay = startDate.clone().add(i, 'day');
        days.push(nextDay);
      }

      return days;
    },

  },

  methods: {
  goToPreviousDay() {
      this.localSelectedMonth = this.localSelectedMonth ? this.localSelectedMonth.clone().subtract(1, 'day') : this.selectedMonth.clone().subtract(1, 'day');
    },
    goToNextDay() {
      this.localSelectedMonth = this.localSelectedMonth ? this.localSelectedMonth.clone().add(1, 'day') : this.selectedMonth.clone().add(1, 'day');
    },
    changeLocalSelectedDay(day) {
      this.localSelectedDay = day;
        this.$emit('local-selected-day-changed', day);
    }
  },
  

  mounted(){
    this.localSelectedDay = this.localSelectedMonth ? this.localSelectedMonth : this.selectedMonth;
  }
};


</script>

<style scoped>

</style>
