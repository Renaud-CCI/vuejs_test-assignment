<template>
 <h2>Month: {{ selectedMonth || currentDate }}</h2>
 <ul>
    <li v-for="day in days" :key="day">{{ day }}</li>
  </ul>
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
    };
  },
  computed: {
    days() {
      if (!this.selectedMonth && !this.currentDate) {
        return ["12", "13", "14", "15"];
      }

      const startDate = this.selectedMonth ? moment(this.selectedMonth).startOf('month') : moment(this.currentDate);
      const days = [startDate.format('D')];

      // Générer les trois prochains jours
      for (let i = 1; i < 4; i++) {
        days.push(startDate.add(1, 'day').format('D'));
      }

      return days;
    },
  },
  mounted(){
    console.log(this.selectedMonth);
  }
};


</script>

<style scoped>

</style>
