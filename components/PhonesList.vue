<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "PhonesList"
})
</script>

<template>
  <div class="phones">
    <a href="tel:380990006461" class="phone">
      <Icon name="iconoir:phone" color="white"></Icon>
      (099)000-64-61
    </a>
  </div>
</template>

<style scoped lang="scss">

</style>