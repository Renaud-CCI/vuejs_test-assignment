<template>
  <div class="app-header-avatar">
    <img :src="dbData.avatar_url" alt="avatar" class="w-16 sm:w-20 h-auto mx-auto mt-2 rounded-full"/>
    <p class="text-base sm:text-xxl">{{ dbData.first_name }}</p>
    <p class="lastName uppercase text-base sm:text-xxl">{{ dbData.last_name }}</p>
  </div>
</template>

<script>
import db from '@/json/db.json';

export default {
  name: 'ProfilePicture',
  data() {
    return {
      dbData: db,
    };
  }
}
</script>

<style scoped>
.lastName{
  margin-top: -5px;
}
</style>