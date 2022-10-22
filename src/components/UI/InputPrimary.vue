<template>
  <input :value="modelValue" @input="updateInput" class="input" />
</template>
<script>
export default {
  name: "InputPrimary",
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
  padding: 0.2em 0.5em;
  width: 100%;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  background-color: var(--clr-secondary-300);
}
</style>
