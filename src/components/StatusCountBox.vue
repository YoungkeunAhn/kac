<script>
export default {
  props: {
    info: Object,
  },
}
</script>
<template>
  <div class="info" :style="{ backgroundColor: info.color }">
    <div class="title">{{ info.title }}</div>
    <div class="count">{{ info.count }}</div>
  </div>
</template>
<style scoped lang="scss">
.info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  padding: 1rem;
  border-radius: 10px;

  font-size: 1.5rem;
  color: #fff;
  letter-spacing: -0.76px;
  font-weight: 500;
}
.title {
  font-size: 1.5rem;
  font-weight: bold;
}
.count {
  font-size: 2.375rem;
  font-weight: 500;
  letter-spacing: -0.76px;
}
</style>
