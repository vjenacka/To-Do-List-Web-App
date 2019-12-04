<template>
  <div class="container">
    <div class="add-item">
      <div class="add-icon" @click="addItem">
        <i class="fas fa-plus"></i>
      </div>
      <form @submit.prevent="addItem">
        <input type="text" placeholder="Add a to-do..." v-model="entry" />
      </form>
      <div class="feature-icon">
        <i v-if="!entryFavorite" class="far fa-star" @click="entryFavorite = !entryFavorite"></i>
        <i v-else class="fas fa-star" @click="entryFavorite = !entryFavorite"></i>
      </div>
    </div>
    <div class="todo-list">
      <div class="item" v-for="(item,index) in todoList" :key="index" :class="{'show':item.show}">
        <div class="item-checkbox">
          <i class="fas fa-square"></i>
        </div>
        <div class="item-title">{{item.title}}</div>
        <div class="feature-icon">
          <i v-if="!item.favorite" class="far fa-star" @click="item.favorite = !item.favorite"></i>
          <i v-else class="fas fa-star" @click="item.favorite = !item.favorite"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data: () => {
    return {
      entry: "",
      entryFavorite: false,
      todoList: []
    };
  },
  methods: {
    addItem() {
      if (this.entry !== "") {
        let date = new Date();
        let newEntry = {
          id: date.getTime(),
          title: this.entry,
          favorite: this.entryFavorite,
          complete: false,
          show: false
        };

        if (newEntry.favorite) {
          //push new item on first position
          this.todoList.splice(0, 0, newEntry);
        } else {
          // push new item on last position
          this.todoList.push(newEntry);
        }
        //will 'transition' the element when found and display it on the list
        setTimeout(() => {
          this.todoList.find(element => element.id === newEntry.id).show = true;
        }, 10);
      }

      this.entry = "";
      this.entryFavorite = false;
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100% - 20px);

  @mixin feature-icon($color) {
    grid-column-start: 3;
    grid-column-end: 3;
    display: flex;
    justify-content: center;
    align-items: center;
    color: $color;
    font-size: 2rem;
    cursor: pointer;
  }

  //form for adding to-dos
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
      @include feature-icon(#fff);
    }
  }

  //todo list styling
  .todo-list {
    padding-top: 20px;

    //single todo
    .item {
      display: grid;
      grid-template-columns: 70px auto 70px;
      grid-template-rows: 60px;
      width: 100%;
      height: 60px;
      margin-bottom: 2px;
      background: rgba($color: #fff, $alpha: 0.8);
      border-radius: 5px;
      overflow: hidden;
      opacity: 0;
      transition: all 0.5s linear;
      .item-checkbox {
        grid-column-start: 1;
        grid-column-end: 1;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 1.6rem;
        color: #99c191;
        cursor: pointer;
      }
      .item-title {
        grid-column-start: 2;
        grid-column-end: 2;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        font-size: 1.6rem;
      }

      .feature-icon {
        @include feature-icon(#333);
      }
    }

    .show {
      opacity: 1;
    }
  }
}
</style>