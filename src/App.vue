<template>
  <main class="app">
    <section aria-label="posts" class="container">
      <form class="form offset">
        <h3 class="form__title">Create Post</h3>
        <input class="form__input" type="text" placeholder="Название" />
        <input class="form__input" placeholder="Описание" />
        <button class="form__button">Submit</button>
      </form>
      <ul class="posts offset">
        <li class="post" v-for="post in posts" :key="post.id">
          <h5 class="post__title">
            {{ post.title }}
          </h5>
          <p class="post__description">
            {{ post.body }}
          </p>
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "Title 1", body: "Description 1" },
        { id: 2, title: "Title 2", body: "Description 2" },
        { id: 3, title: "Title 3", body: "Description 3" },
      ],
    };
  },
  methods: {},
};
</script>

<style>
/* RESET */
*,
:after,
:before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style-type: none;
  outline: none;
  border: none;
  background: inherit;
  color: inherit;
  font: inherit;
  scroll-behavior: smooth;
  text-rendering: optimizeSpeed;
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

body {
  color: var(--clr-primary);
  background-color: var(--clr-secondary-400);
  font-size: var(--fs-400);
  font-family: monospace, sans-serif;
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
.app {
  color: var(--clr-primary-300);
}

/* FORM */
.form {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;
}

.form__title {
  font-size: var(--fs-700);
  font-weight: var(--fw-700);
}

.form__input {
  padding: 0.2em 0.5em;
  width: 100%;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  background-color: var(--clr-secondary-300);
}

.form__button {
  margin-top: 0.5rem;
  padding: 0.2em 1.3em;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  cursor: pointer;
  font-weight: var(--fw-700);
  color: var(--clr-secondary-400);
  background-color: var(--clr-accent-400);

  transition: all 0.3s;
}

.form__button:hover {
  color: var(--clr-primary);
}

/* POSTS */
.posts {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.post {
  padding: 1rem;
  box-shadow: 0 0.25em 1em rgb(0 0 0 / 35%);
  border-radius: 0.5rem;
  background-color: var(--clr-secondary-300);
}

.post__title {
  font-size: var(--fs-600);
}

.post__title::first-letter {
  color: var(--clr-accent-400);
}
</style>
