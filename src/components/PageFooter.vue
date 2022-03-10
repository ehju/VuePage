<template>
  <footer class="footer mt-auto py-3 bg-light">
    <div class="container clearAllContainter">
      <span class="text-muted clearAllBtn" @click="clearAllTodo"
        >Clear Everything</span
      >
    </div>
  </footer>
</template>

<script>
export default {
  methods: {
    clearAllTodo() {
      this.$emit("clearAllTodo");
    },
  },
};
</script>

<style>
</style>