<template>
  <li class="post">
    <header aria-label="post-header" class="header">
      <h4 class="title">{{ post.title }}</h4>
      <ButtonDelete @click="$emit('delete', post)" />
    </header>
    <p class="description">{{ post.body }}</p>
    <!-- <ButtonDelete @click="$emit('delete', post)" /> -->
  </li>
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
  flex-direction: column;
  gap: 1rem;
  background-color: var(--clr-secondary-300);
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.title {
  max-width: 90%;
  padding-bottom: 0.75rem;
  border-bottom: 2px solid var(--clr-accent-400);
  font-size: var(--fs-600);
}

.title::first-letter {
  text-transform: uppercase;
  color: var(--clr-accent-400);
}

.description {
  max-width: 90%;
}

.description::first-letter {
  text-transform: uppercase;
}
</style>
