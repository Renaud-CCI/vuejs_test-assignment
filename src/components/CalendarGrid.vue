<template>
  <div class="grid grid-rows-96 gap-0" style="grid-template-rows: repeat(96, 20px);">
    <div v-for="hour in 96" :key="hour" class="border-t-2 border-red-500 row-span-1">{{ hour%4==0 || hour==1 ? hourToTime(hour) : '' }}</div>
  </div>
</template>



<script>


export default {
  name: 'CalendarGrid',
  components: {
    
  },  
  methods:{
    hourToTime(hour) {
      const hourStart = Math.floor(hour / 4);
      const minutes = (hour % 4) * 15;
      return `${hourStart.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}`;
    },
  }
};


</script>

<style scoped>

</style>