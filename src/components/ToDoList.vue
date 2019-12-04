<template>
  <div class="container">
    <div class="add-item">
      <div class="add-icon">
        <i class="fas fa-plus"></i>
      </div>
      <form action="#">
        <input type="text" placeholder="Add a to-do..." />
      </form>
      <div class="feature-icon">
          <i class="far fa-star"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList"
};
</script>

<style lang="scss" scoped>
</style>