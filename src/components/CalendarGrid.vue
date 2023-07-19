<template>
  <div class="grid grid-rows-96 gap-0 relative" style="grid-template-rows: repeat(96, 16px);">
    <div v-for="hour in 96" :key="hour" :class="((hour-1)%4==0 || hour==0) ? 'border-t-2 border-gray-300 row-span-1' : 'row-span-1'">
    </div>
    <!-- <div :style="`top: ${ startTimeInFloat * 64 }px; height: ${(endTimeInFloat - startTimeInFloat) * 64}px`" class="absolute left-1/2 bg-purple-700 text-white w-4/5 rounded-md transform -translate-x-1/2">
    Test 10h-11h20 {{selectedDay.format('MMM')}}
    </div> -->
    <TaskCard :selected-day="selectedDay"/>
  </div>
</template>

<script>
import moment from 'moment';
import TaskCard from './TaskCard.vue';

export default {
  name: 'CalendarGrid',
  props: {
    selectedDay: {
      type: moment,
      default: null,
    },
  },
  components: {
    TaskCard,
  },
  data() {
    return {
    };
  },

};
</script>

<style scoped>

</style>