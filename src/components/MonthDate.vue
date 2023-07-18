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
    const startDate = this.selectedMonth ? moment(this.selectedMonth) : moment(this.currentDate);
    const days = [startDate.clone()];

    // Générer les trois prochains jours
    for (let i = 1; i < 4; i++) {
      const nextDay = startDate.clone().add(i, 'day');
      days.push(nextDay);
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
