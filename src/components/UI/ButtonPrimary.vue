<template>
  <button class="button"><slot></slot></button>
</template>
<script>
export default {
  name: "ButtonPrimary",
};
</script>
<style scoped>
.button {
  padding: 0.5em 1.3em;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  font-weight: var(--fw-700);
  color: var(--clr-secondary-400);
  background-color: var(--clr-accent-400);
  cursor: pointer;
  transition: all 0.3s;
}

.button:hover,
.button:focus-visible {
  color: var(--clr-primary);
}
</style>
