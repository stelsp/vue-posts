<template>
  <form @submit.prevent class="form offset">
    <h3 class="title">Create Post</h3>
    <InputPrimary v-model="post.title" type="text" placeholder="Title" />
    <InputPrimary v-model="post.body" type="text" placeholder="Description" />
    <ButtonPrimary @click="createPost">Submit</ButtonPrimary>
  </form>
</template>
<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>
<style scoped>
.form {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
}

.title {
  font-size: var(--fs-700);
  font-weight: var(--fw-700);
}

.button {
  margin-top: 1rem;
}
</style>
