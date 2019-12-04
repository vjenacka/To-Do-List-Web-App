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
.container {
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100% - 20px);

  .add-item {
    display: grid;
    grid-template-columns: 70px auto 70px;
    grid-template-rows: 60px;
    width: 100%;
    height: 60px;
    background: rgba($color: #000000, $alpha: 0.3);
    border-radius: 5px;
    overflow: hidden;

    .add-icon {
      grid-column-start: 1;
      grid-column-end: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #fff;
      font-size: 2rem;
      cursor: pointer;
    }

    input {
      grid-column-start: 2;
      grid-column-end: 2;
      background: none;
      border: none;
      width: 100%;
      height: 60px;
      color: #fff;
      font-size: 1.6rem;

      &::placeholder {
        color: #fff;
      }
      &:focus {
        outline: none;
      }
    }

    .feature-icon {
      grid-column-start: 3;
      grid-column-end: 3;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #fff;
      font-size: 2rem;
      cursor: pointer;
    }
  }
}
</style>