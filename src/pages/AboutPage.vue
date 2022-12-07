<template>
  <header class="container section-header offset">
    <h1 class="title">About Page</h1>
    <nav class="nav">
      <router-link to="/posts">Posts</router-link>
      <router-link to="/">Main</router-link>
    </nav>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
.nav {
  margin-inline: auto;
  display: flex;
  gap: 3rem;
}

.nav router-link:hover {
  border-bottom: 1px solid var(--clr-accent-300);
}
</style>
