<template>
  <div>
    <p class="loading">
      Loading
      <span class="loading__dot-1">.</span>
      <span class="loading__dot-2">.</span>
      <span class="loading__dot-3">.</span>
    </p>
  </div>
</template>

<script>
export default {
  name: "LoadingPrimary",
};
</script>

<style scoped>
@keyframes blink {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
.loading__dot-1 {
  animation: blink 0.5s infinite;
}
.loading__dot-2 {
  animation: blink 0.6s infinite;
}
.loading__dot-3 {
  animation: blink 0.7s infinite;
}
</style>
