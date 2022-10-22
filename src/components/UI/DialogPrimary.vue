<template>
  <div v-if="show" @click="$emit('update:show', false)" class="dialog">
    <div @click.stop class="content">
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  name: "DialogPrimary",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
<style scoped>
.dialog {
  position: fixed;
  inset: 0;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  background: rgb(0 0 0 / 0.4);
}

.content {
  margin-top: 10vh;
  border-radius: 0.5rem;
  padding: 1rem;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  background-color: var(--clr-secondary-300);
}
</style>
