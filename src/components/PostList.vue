<template>
  <div v-if="posts.length > 0" class="wrapper offset">
    <h3 class="title">Posts</h3>
    <transition-group name="posts" tag="ul" class="posts">
      <PostItem
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @delete="$emit('delete', post)"
      />
    </transition-group>
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
  overflow: hidden;
}

.title {
  font-size: var(--fs-700);
  font-weight: var(--fw-700);
}

.posts-enter-active,
.posts-leave-active {
  transition: all 0.4s;
}
.posts-enter-from,
.posts-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.posts-move {
  transition: transform 0.8s ease;
}
</style>
