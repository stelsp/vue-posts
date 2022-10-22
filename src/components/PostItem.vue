<template>
  <div class="post">
    <li>
      <h5 class="title">
        {{ post.title }}
      </h5>
      <p class="description">
        {{ post.body }}
      </p>
    </li>
    <ButtonDelete />
  </div>
</template>
<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style scoped>
.post {
  padding: 1rem;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  background-color: var(--clr-secondary-300);
}

.title {
  font-size: var(--fs-600);
}

.title::first-letter {
  color: var(--clr-accent-400);
}
</style>
