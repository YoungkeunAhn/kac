<script>
export default {
  props: {
    info: Object,
  },
}
</script>
<template>
  <div class="item content-item-box">
    <div class="caption">{{ info.caption }}</div>
    <div class="subject">{{ info.subject }}</div>
    <div class="value">{{ info.value }}</div>
  </div>
</template>
<style lang="scss" scoped>
.content-item-box {
  padding: 1.125rem 1.75rem;
}
.caption,
.subject {
  color: #9bb8ff;
}

.caption {
  font-size: 1.188rem;
  font-weight: 500;
  letter-spacing: -0.57px;
  word-break: keep-all;
  white-space: nowrap;
}

.subject {
  margin-top: 0.313rem;
  font-size: 1.5rem;
  font-weight: 600;
  word-break: keep-all;
  white-space: nowrap;
}

.value {
  margin-top: 0.5rem;
  font-size: 2.375rem;
  font-weight: 500;
  letter-spacing: -0.76px;
}

.weather-img-wrap {
  width: 50px;
}
.weather-values {
  font-size: 0.9rem;
}
</style>
