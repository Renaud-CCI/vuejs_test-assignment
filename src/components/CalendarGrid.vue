<template>
  <div class="grid grid-rows-96 gap-0 relative" style="grid-template-rows: repeat(96, 16px);">
    <div v-for="hour in 96" :key="hour" :class="((hour-1)%4==0 || hour==0) ? 'border-t-2 border-gray-300 row-span-1' : 'row-span-1'">
    </div>

    <div class="absolute top-4 left-2 h-4 bg-blue-500">01</div>
    <div :style="`top: ${ startTimeInFloat * 64 }px; height: ${(endTimeInFloat - startTimeInFloat) * 64}px`" class="absolute left-2 bg-green-500">Test 10h-11h20</div>
  </div>
</template>

<script>
import db from '@/json/db.json';

export default {
  name: 'CalendarGrid',
  data() {
    return {
      dbData: [],
      startTimeInFloat:null,
      endTimeInFloat:null 
    };
  },
  created() {
    this.dbData = db;
    this.dbData.tasks.forEach(element => {
        this.startTimeInFloat = this.timeInFloat(JSON.parse(JSON.stringify(element))['start-time']);
        this.endTimeInFloat = this.timeInFloat(JSON.parse(JSON.stringify(element))['end-time']);
    });
    console.log('ppl2', this.startTimeInFloat, this.endTimeInFloat);
}, 
  methods:{
    hourToTime(hour) {
      const hourStart = Math.floor(hour / 4);
      const minutes = (hour % 4) * 15;
      return `${hourStart.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}`;
    },
    timeInFloat(time){
        let [hour, minute] = time.split(':'); // Séparation des heures et des minutes
        return ((parseInt(hour)) + (parseInt(minute) / 60)).toFixed(2); // Conversion en float
    }
  }
};
</script>

<style scoped>

</style>