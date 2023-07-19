<template>
  <div class="grid grid-rows-96 gap-0" style="grid-template-rows: repeat(96, 16px);">
    <div v-for="hour in 96" :key="hour" :class="((hour-1)%4==0 || hour==0) ? 'border-t-2 border-gray-300 row-span-1' : 'row-span-1'">
      {{ (hour-1)%4==0 || hour==0 ? hourToTime(hour) : '' }}
    </div>
  </div>
</template>



<script>


export default {
  name: 'CalendarHours',
  components: {
    
  },  
  methods:{
    hourToTime(hour) {
      let testHour = hour-1;
      const hourStart = Math.floor(testHour / 4);
      const minutes = (testHour % 4) * 15;
      return `${hourStart.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}`;
    },
  }
};


</script>

<style scoped>

</style>