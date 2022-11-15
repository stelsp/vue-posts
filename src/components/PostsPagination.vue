<template>
  <div class="container offset wrapper">
    <!-- <ul class="pagination__wrapper">
      <li
        v-for="pagination in totalPages"
        :key="pagination"
        @click="$emit('change', pagination)"
        class="pagination"
        :class="{ pagination__current: page === pagination }"
      >
        {{ pagination }}
      </li>
    </ul>
    <ButtonPrimary @click="$emit('toggle', scroll)" type="button">
      Load All Post's
    </ButtonPrimary> -->
  </div>
</template>
<script>
export default {
  props: {
    totalPages: {
      type: Number,
    },
    page: {
      type: Number,
    },
    scroll: {
      type: Boolean,
    },
  },
};
</script>
<style scoped>
.button {
  padding: 0.5rem 1rem;
}
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}
.pagination__wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  margin-inline: auto;
}

.pagination {
  cursor: pointer;
}

.pagination:hover,
.pagination:focus-visible {
  scale: 1.2;
  color: var(--clr-accent-400);
}

.pagination:active {
  scale: 1.3;
}

.pagination__current {
  color: var(--clr-accent-400);
}
</style>
