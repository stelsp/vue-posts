<template>
  <form @submit.prevent class="form offset">
    <h3 class="title">Create Post</h3>
    <input v-model="post.title" type="text" placeholder="Title" class="input" />
    <input
      v-model="post.body"
      type="text"
      placeholder="Description"
      class="input"
    />
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

.input {
  padding: 0.2em 0.5em;
  width: 100%;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  background-color: var(--clr-secondary-300);
}
</style>
