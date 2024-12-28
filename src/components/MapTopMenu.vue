<script>
import MainButton from './MainButton.vue'
import MapTopMenuItems from './MapTopMenuItems.vue'

export default {
  components: { MainButton },
  props: {
    menuList: Array,
  },
  data() {
    return {}
  },
}
</script>
<template>
  <div v-for="menu in menuList" class="menu">
    <MainButton class="main-btn" :label="menu.title" />
    <MapTopMenuItems :items="menu.items" />
  </div>
</template>
<style scoped lang="scss">
.menu {
  button + button {
    margin-left: 1.125rem;
  }
}
</style>
