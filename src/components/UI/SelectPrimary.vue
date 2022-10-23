<!-- eslint-disable vue/no-mutating-props -->
<template>
  <select v-model="modelValue" @change="changeOption" class="select">
    <option disabled selected value="">Choose from list</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>
<script>
export default {
  name: "SelectPrimary",
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    changeOption(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>
<style scoped>
.select {
  padding: 0.2em 1em;
  background-color: var(--clr-secondary-300);
  border-radius: 0.5rem;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  font-weight: var(--fw-700);
  color: var(--clr-accent-400);
  cursor: pointer;
}
</style>
