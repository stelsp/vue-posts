<template>
  <input :value="modelValue" @input="updateInput" class="input" />
</template>
<script>
export default {
  name: "InputSecondary",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
<style scoped>
.input {
  padding: 1em;
  width: 100%;
  border-radius: 0.5rem 0.5rem 0 0;
  border-bottom: 2px solid var(--clr-accent-400);
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  font-weight: var(--fw-700);
  background-color: var(--clr-secondary-300);
}
</style>
