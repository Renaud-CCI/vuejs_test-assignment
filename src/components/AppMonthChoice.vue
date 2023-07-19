<template>
  <div class="flex items-center justify-center space-x-4 my-5">
    <p
      v-for="(month, index) in months"
      :key="month"
      @click="selectMonth(month)"
      :class="{
        'font-bold text-xl': month === selectedMonth,
        'w-1/5': true,
        'text-right cursor-pointer': index === 2,
        'text-left cursor-pointer': index === 0,
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
  props: {
    currentDate: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      selectedMonth: this.currentDate,
      arrowLeftIcon: faArrowLeft,
      arrowRightIcon: faArrowRight,
    };
  },
  computed: {
    months() {
      const previousMonth = moment(this.selectedMonth).subtract(1, 'month');
      const nextMonth = moment(this.selectedMonth).add(1, 'month');

      return [previousMonth, this.selectedMonth, nextMonth];
    },
  },
  methods: {
    selectMonth(month) {
      this.selectedMonth = month;
      this.$emit('month-selected', this.selectedMonth);
    },
  },

};
</script>

<style scoped>

</style>
