<template>
<div class="grid grid-cols-3 gap-4 items-center">

    <AppHeaderArrow />

  <div class="col-span-1 justify-center flex items-start">
    <img src="../assets/logo_highday.png" alt="highday logo" class="rounded-full w-20 sm:w-1/4 my-1">
  </div>
  <div class="col-span-1 justify-end">
    <ProfilePicture />
  </div>
</div>
</template>

<script>
import AppHeaderArrow from './AppHeaderArrow.vue'
import ProfilePicture from './ProfilePicture.vue';

export default {
  name: 'AppHeader',
  components: {
    AppHeaderArrow,
    ProfilePicture
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
