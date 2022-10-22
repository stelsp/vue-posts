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
  padding-block: 0.2em;
  width: 100%;
  border-bottom: 1px solid var(--clr-accent-400);
  background-color: var(--clr-secondary-300);
}
</style>
