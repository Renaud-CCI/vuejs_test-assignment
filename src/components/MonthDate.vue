<template>
<div class="grid grid-cols-6 gap-3 items-center">
    <div class="flex justify-end">
      <font-awesome-icon :icon="arrowLeftIcon" class="clickable" @click="goToPreviousDay"/>
    </div>
    <div v-for="day in days" :key="day" class="bg-white hover:bg-purple-800 text-purple-800 hover:text-white rounded-full h-20 w-14 sm:h-40 sm:w-32 mx-auto flex flex-col justify-center items-center">
      <p class="text-xl font-bold">{{ day.format('D') }}</p>
      <p>{{ day.format('ddd') }}</p>
    </div>
    <div class="flex justify-start">
      <font-awesome-icon :icon="arrowRightIcon" class="clickable" @click="goToNextDay"/>
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
    };
  },
  computed: {
    days() {
console.log('currentDate : ', this.currentDate, 'selectedMonth : ', this.selectedMonth, 'localSelectedMonth : ', this.localSelectedMonth);

      const startDate = this.localSelectedMonth ? moment(this.localSelectedMonth) : this.selectedMonth ? moment(this.selectedMonth) : moment(this.currentDate);
      const days = [startDate.clone()];

      // Générer les trois prochains jours
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
    }
  },
  

  mounted(){
    console.log(this.selectedMonth);
  }
};


</script>

<style scoped>
.clickable {
  cursor: pointer;
}
</style>
