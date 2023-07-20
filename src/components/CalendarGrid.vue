<template>
  <div class="grid grid-rows-24 gap-0 relative" style="grid-template-rows: repeat(24, 60px);">
    <!-- Make a grid with 24 rox=ws for 24 hours and a height of 60px for 60 minutes/hours-->
    <div v-for="hour in 24" :key="hour" class="border-t-2 border-gray-300 row-span-1">
    </div>
    <!-- Place for absolutes TaskCards -->
    <TaskCard :selected-day="selectedDay" :jsonData="jsonData"/>
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
    jsonData: {
      type: Object,
      required: true,
    },
  },
  components: {
    TaskCard,
  },

};
</script>

<style scoped>

</style>