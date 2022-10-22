<template>
  <div v-if="posts.length > 0" class="wrapper offset">
    <h3 class="title">Posts</h3>
    <ul class="posts">
      <PostItem
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @delete="$emit('delete', post)"
      />
    </ul>
  </div>
  <div v-else class="wrapper offset">
    <h3 class="title">Posts Empty</h3>
  </div>
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
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
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
