<template>
  <div class="app-header-avatar">
    <img :src="jsonData.avatar_url" alt="avatar" class="w-16 sm:w-20 h-auto mx-auto mt-2 rounded-full border-2 border-white"/>
    <p class="text-base sm:text-xxl">{{ jsonData.first_name }}</p>
    <p class="lastName uppercase text-base sm:text-xxl">{{ jsonData.last_name }}</p>
  </div>
</template>

<script>

export default {
  name: 'ProfilePicture',
  props: {
    jsonData: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style scoped>
.lastName{
  margin-top: -5px;
}
</style>