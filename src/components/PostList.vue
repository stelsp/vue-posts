<template>
  <div>
    <h3 class="title">Posts</h3>
  </div>
  <ul class="posts offset">
    <PostItem
      v-for="post in posts"
      :key="post.id"
      :post="post"
      @delete="$emit('delete', post)"
    />
  </ul>
</template>
<script>
import PostItem from "./PostItem.vue";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.posts {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.title {
  font-size: var(--fs-700);
  font-weight: var(--fw-700);
}
</style>
