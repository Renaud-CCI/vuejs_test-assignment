<template>
  <div class="grid grid-rows-24 gap-0 relative" style="grid-template-rows: repeat(24, 60px);">
    <div v-for="hour in 24" :key="hour" class="border-t-2 border-gray-300 row-span-1">
    </div>
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