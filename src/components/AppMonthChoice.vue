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
      {{ month.format('MMM') }}
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
      currentDate: "2022-02-12",
      selectedMonth: null,
      arrowLeftIcon: faArrowLeft,
      arrowRightIcon: faArrowRight,
    };
  },
  computed: {
    currentMonth() {
      return moment(this.currentDate);
    },
    months() {
      const previousMonth = moment(this.currentDate).subtract(1, 'month');
      const nextMonth = moment(this.currentDate).add(1, 'month');

      return [previousMonth, this.currentMonth, nextMonth];
    },
  },
  methods: {
    selectMonth(month) {
      this.currentDate = month;
      this.$emit('month-selected', this.currentDate);
    },
  },

};
</script>

<style scoped>
p {
  cursor: pointer;
}
</style>
