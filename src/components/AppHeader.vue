<template>
<div class="grid grid-cols-3 gap-4 items-center">

    <HeaderArrow />

  <div class="col-span-1 justify-center flex items-start">
    <img src="../assets/logo_highday_transp.png" alt="highday logo" class="rounded-full w-20 sm:w-1/4 my-1 border-2 border-purple-500">
  </div>
  <div class="col-span-1 justify-end">
    <ProfilePicture :jsonData="jsonData"/>
  </div>
</div>
</template>

<script>
import HeaderArrow from './HeaderArrow.vue'
import ProfilePicture from './ProfilePicture.vue';

export default {
  name: 'AppHeader',
  props: {
    jsonData: {
      type: Object,
      required: true,
    },
  },
  components: {
    HeaderArrow,
    ProfilePicture
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
