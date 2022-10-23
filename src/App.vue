<template>
  <main class="app">
    <section aria-label="section-posts" class="container">
      <header aria-label="section-posts-header" class="section-header offset">
        <h1 class="title">Posts App</h1>
        <div>
          <SelectPrimary v-model="selectedSort" :options="sortOptions" />
          <ButtonPrimary @click="showDialog" type="button">
            Create Post
          </ButtonPrimary>
        </div>
      </header>
      <PostList :posts="posts" v-if="!isPostsLoading" @delete="deletePost" />
      <LoadingPrimary v-if="isPostsLoading" class="title offset" />
      <DialogPrimary v-model:show="dialogVisible">
        <PostForm @create="createPost" />
      </DialogPrimary>
    </section>
  </main>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import axios from "axios";

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: () => [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "Title" },
        { value: "body", name: "Body" },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts = [post, ...this.posts];
      this.dialogVisible = false;
    },
    deletePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        this.posts = response.data;
      } catch (e) {
        alert("Ошибка");
      } finally {
        this.isPostsLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
/* RESET  */
*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0;
  padding: 0;
  font: inherit;
  color: inherit;
  background: inherit;
  outline: none;
  border: none;
}

ul,
ol {
  list-style: none;
}

html {
  scroll-behavior: smooth;
}

html:focus-within {
  scroll-behavior: smooth;
}

body {
  min-height: 100vh;
  text-rendering: optimizeSpeed;
}

a {
  text-decoration: inherit;
}

img,
picture,
svg {
  display: block;
}

@media screen and (prefers-reduced-motion: reduce) {
  html {
    scroll-behavior: auto;
  }
}

@media (prefers-reduced-motion: reduce) {
  html:focus-within {
    scroll-behavior: auto;
  }

  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

:root {
  --clr-primary: #fff;
  --clr-primary-300: rgba(255, 255, 255, 0.8);
  --clr-accent-300: #a9f0e2;
  --clr-accent-400: #0fc5b0;
  --clr-accent-500: #00937e;
  --clr-accent-600: #0a4039;
  --clr-secondary-200: #434956;
  --clr-secondary-300: #272a2e;
  --clr-secondary-400: #222529;
  --clr-secondary-500: #1d1e20;
  --fw-300: 300;
  --fw-400: 400;
  --fw-700: 700;
  --fs-100: 0.64rem;
  --fs-200: 0.8rem;
  --fs-300: 1.125rem;
  --fs-400: 1.325rem;
  --fs-500: 1.563rem;
  --fs-600: 1.563rem;
  --fs-700: 2rem;
  --fs-800: 2.5rem;
  --fs-900: 3.2rem;
  --fs-xl: clamp(4.5rem, 1rem + 8vw, 9rem);
  --ff-accent: "Roboto", sans-serif;
  --ff-primary: monospace, sans-serif;
  --spacer: 2rem;
  --linear-gradient: linear-gradient(
    90deg,
    var(--clr-secondary-300),
    var(--clr-secondary-400)
  );
  --glow-gradient: radial-gradient(
    var(--clr-secondary-300),
    var(--clr-secondary-400)
  );
}

/* UTILITY */
.container {
  --max-width: 1200px;
  --padding: 1rem;
  width: min(var(--max-width), 100% - (var(--padding) * 2));
  margin-inline: auto;
}

.offset {
  padding-block: 1rem;
}

/* APP */
body {
  min-width: 320px;
  color: var(--clr-primary);
  background-color: var(--clr-secondary-400);
  font-size: var(--fs-400);
  font-family: monospace, sans-serif;
}

.section-header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
}
.section-header div {
  width: 100%;

  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.app {
  color: var(--clr-primary-300);
}

.title {
  font-size: var(--fs-700);
  font-weight: var(--fw-700);
}
</style>
