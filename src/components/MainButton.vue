<script>
export default {
  props: {
    label: String,
    class: String,
  },
}
</script>
<template>
  <button class="main-btn" :class="class">{{ label }}</button>
</template>
<style lang="scss" scoped>
.main-btn {
  cursor: pointer;
  font-size: 2rem;

  padding: 1.5rem 0;
  box-sizing: border-box;
  border-radius: 10px;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.2),
    rgba(34, 34, 34, 0)
  );
  background-color: #222;
  color: #766626;
  border: none;
  width: 100%;
}

.main-btn:hover {
  background: linear-gradient(90deg, #4a3d09 2%, #222);
  color: #c9aa2b;
  font-weight: 500;
  border: none;
}
</style>
