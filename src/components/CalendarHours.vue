<template>
  <div class="grid grid-rows-24 gap-0" style="grid-template-rows: repeat(24, 60px);">
    <!-- Make a grid with 24 rows for 24 hours and a height of 60px for 60 minutes/hours, then display hours in each row-->
    <div v-for="hour in 24" :key="hour" class="border-t-2 border-gray-300 row-span-1 flex justify-center">
      <p class="hourParagraph">{{ hour-1 + ':00'}}</p>
    </div>
  </div>
</template>



<script>


export default {
  name: 'CalendarHours',
  components: {
    
  },  
  methods:{
  }
};


</script>

<style scoped>
.hourParagraph{
  margin:-12px;
  width: fit-content;
  background-color: #DBE9F6;
}
</style>