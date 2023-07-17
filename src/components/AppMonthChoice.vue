<template>
  <div class="flex items-center justify-center space-x-4 my-5">
    <p
      v-for="(month, index) in months"
      :key="month"
      @click="selectMonth(month)"
      :class="{
        'font-bold': month === currentMonth,
        'w-1/5': true,
        'text-right': index === 2,
        'text-left': index === 0,
        'text-xl': true
      }"
    >
      <font-awesome-icon
        v-if="index === 0"
        :icon="index === 0 ? arrowLeftIcon : arrowRightIcon"
        class="mr-1"
      />
      {{ month }}
      <font-awesome-icon
        v-if="index === 2"
        :icon="index === 2 ? arrowRightIcon : arrowLeftIcon"
        class="ml-1"
      />
    </p>
  </div>
</template>



<script>
import moment from 'moment'
import { faArrowLeft, faArrowRight } from '@fortawesome/free-solid-svg-icons';

export default {
  name: 'AppMonthChoice',
  data() {
    return {
      currentDate: moment("2022-02-12"),
      selectedMonth: null,
      arrowLeftIcon: faArrowLeft,
      arrowRightIcon: faArrowRight,
    };
  },
  computed: {
    currentMonth() {
      return this.currentDate.format('MMM');
    },
    months() {
      const previousMonth = this.currentDate.clone().subtract(1, 'month').format('MMM');
      const nextMonth = this.currentDate.clone().add(1, 'month').format('MMM');
      return [previousMonth, this.currentMonth, nextMonth];
    },
  },
  methods: {
    selectMonth(month) {
      this.currentDate = moment().month(month);
      this.selectedMonth = month;
      this.$emit('month-selected', month);
    },
  },
};
</script>

<style scoped>
p {
  cursor: pointer;
}
</style>
