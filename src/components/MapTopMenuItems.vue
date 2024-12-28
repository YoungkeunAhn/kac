<script>
export default {
  props: {
    items: Array,
  },
  data() {
    return {}
  },
}
</script>
<template>
  <ul class="sub-menu-list">
    <li v-for="item in items" class="sub-menu">
      <div>
        <img
          v-if="item.icon"
          :src="`/src/assets/icons/${item.icon}.svg`"
          alt=""
          width="38"
          height="38"
        />

        <span>{{ item.name }}</span>
      </div>

      <ToggleSwitch v-model="item.value" style="width: 3rem; height: 2rem" />
    </li>
  </ul>
</template>
<style scoped lang="scss">
.sub-menu-list {
  margin-top: 1.125rem;
  background-color: #222;
  padding: 1rem;
  border-radius: 10px;

  .sub-menu {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 2rem;
    line-height: 1.58;

    color: #fff;

    img {
      margin-right: 1rem;
      //   width: 1.25rem;
      //   height: 1.25rem;
    }

    & > div {
      display: flex;
      align-items: center;
    }
  }

  .sub-menu + .sub-menu {
    margin-top: 1rem;
  }
}
:deep(.p-toggleswitch-handle) {
  top: 29%;
  width: 1.875rem;
  height: 1.875rem;
}
:deep(.p-toggleswitch.p-toggleswitch-checked .p-toggleswitch-slider),
:deep(
    .p-toggleswitch:not(.p-disabled):has(
        .p-toggleswitch-input:hover
      ).p-toggleswitch-checked
      .p-toggleswitch-slider
  ) {
  background: #c9aa2b;
}
</style>
