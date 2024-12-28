<script>
export default {
  props: {
    info: Object,
  },
}
</script>
<template>
  <div class="item content-item-box">
    <div
      class="subject"
      :style="{
        letterSpacing: info.subject === '안전 운행 평균 지수' ? '-4px' : '',
      }"
    >
      {{ info.subject }}
    </div>
    <div class="value">{{ info.value }}</div>
  </div>
</template>
<style lang="scss" scoped>
.content-item-box {
  padding: 2.625rem 0.825rem;
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
  font-size: 1.438rem;
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
