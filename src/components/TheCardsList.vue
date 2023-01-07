
<script>
import TheCardItem from './TheCardItem.vue'

export default {
  components: {
    TheCardItem
  }
}
</script>

<template>
  <ul>
    <TheCardItem />
  </ul>
</template>

<style scoped lang="scss">
ul {
 padding: 0;
 list-style: none;
}
</style>