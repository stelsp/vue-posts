<template>
  <main>
    <section aria-label="section-form">
      <header
        aria-label="section-form-header"
        class="container section-header offset"
      >
        <h1 class="title">Posts App</h1>
        <InputSecondary
          v-model="searchQuery"
          type="text"
          placeholder="Search"
        />
        <div>
          <SelectPrimary v-model="selectedSort" :options="sortOptions" />
          <ButtonPrimary @click="showDialog" type="button">
            Create Post
          </ButtonPrimary>
        </div>
      </header>
      <DialogPrimary v-model:show="dialogVisible">
        <PostForm @create="createPost" />
      </DialogPrimary>
    </section>
    <section aria-label="section-posts">
      <PostList
        v-if="!isPostsLoading"
        :posts="sortedAndSearchedPosts"
        @delete="deletePost"
        class="container"
      />
      <div ref="observer" class="observer" />
      <LoadingPrimary v-if="isPostsLoading" class="title container offset" />
      <PostsPagination
        v-if="!scroll"
        :totalPages="totalPages"
        :page="page"
        :scroll="scroll"
        @change="changePage"
        @toggle="toggleScroll"
      />
    </section>
  </main>
</template>

<script>
import axios from "axios";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import PostsPagination from "@/components/PostsPagination.vue";

export default {
  components: {
    PostForm,
    PostList,
    PostsPagination,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      searchQuery: "",
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "Title" },
        { value: "body", name: "Description" },
      ],
      page: 1,
      limit: 10,
      totalPages: 0,
      scroll: false,
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
    changePage(pageNumber) {
      this.page = pageNumber;
    },
    toggleScroll() {
      this.scroll = !this.scroll;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts",
          {
            params: {
              _page: this.page,
              _limit: this.limit,
            },
          }
        );
        this.totalPages = Math.ceil(
          response.headers["x-total-count"] / this.limit
        );
        this.posts = response.data;
      } catch (e) {
        alert("Ошибка");
      } finally {
        this.isPostsLoading = false;
      }
    },
    async fetchMorePosts() {
      try {
        this.page += 1;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts",
          {
            params: {
              _page: this.page,
              _limit: this.limit,
            },
          }
        );
        this.totalPages = Math.ceil(
          response.headers["x-total-count"] / this.limit
        );
        this.posts = [...this.posts, ...response.data];
      } catch (e) {
        alert("Ошибка");
      }
    },
  },
  mounted() {
    this.fetchPosts();

    const options = {
      rootMargin: "0px",
      threshold: 1.0,
    };

    const callback = (entries) => {
      if (entries[0].isIntersecting && this.page < this.totalPages) {
        this.fetchMorePosts();
      }
    };

    const observer = new IntersectionObserver(callback, options);
    observer.observe(this.$refs.observer);
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) =>
        post1[this.selectedSort]?.localeCompare(post2[this.selectedSort])
      );
    },
    sortedAndSearchedPosts() {
      return this.sortedPosts.filter((post) =>
        post.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>

<style></style>
