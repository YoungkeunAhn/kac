<script>
export default {
  props: {
    label: String,
  },
}
</script>
<template>
  <button class="btn" :class="class">{{ label }}</button>
</template>
<style lang="scss" scoped>
.btn {
  height: 3.75rem;
  cursor: pointer;
  font-size: 1.5rem;

  padding: 1rem 0;
  box-sizing: border-box;
  border-radius: 10px;

  background-color: #222;
  color: #766626;
  border: none;
  width: 100%;
}

.btn:hover {
  background: #c9aa2b;
  color: #222;
  font-weight: 500;
  border: none;
}
</style>
