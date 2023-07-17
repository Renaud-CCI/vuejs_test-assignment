<template>
<div class="grid grid-cols-3 gap-4 items-center">
  <div class="col-span-1 justify-start">
    <AppHeaderArrow />
  </div>
  <div class="col-span-1 justify-center flex items-center">
    <img src="../assets/logo_highday.png" alt="highday logo" class="rounded-full w-1/2">
  </div>
  <div class="col-span-1 justify-end">
    TEST
  </div>
</div>
</template>

<script>
import AppHeaderArrow from './AppHeaderArrow.vue'

export default {
  name: 'AppHeader',
  components: {
    AppHeaderArrow
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
