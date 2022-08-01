<template>
  <div>
    <input type="text" v-model="inputVal" @keydown.enter="addTodoItem" />
    <div class="hello">
      <div
        v-for="item in todoList"
        :key="item.id"
        class="todoBox"
        :class="[item.isFinish ? 'active' : '']"
        @click="() => handleClick(item)"
      >
        {{ item.title }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      inputVal: "",
      todoList: [],
    };
  },
  methods: {
    handleClick(target) {
      const todoItem = this.todoList.find((item) => item.id === target.id);
      todoItem.isFinish = !todoItem.isFinish;
    },
    addTodoItem() {
      const payload = {
        id: Math.random(),
        title: this.inputVal,
        isFinish: false,
      };
      this.todoList.push(payload);
      this.inputVal = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todoBox {
  border: 1px solid rgb(185, 185, 185);
  padding: 10px;
  min-width: 100px;
  margin: 5px;
  box-shadow: 5px 5px 5px rgb(212, 211, 211);
}
.todoBox:hover {
  cursor: pointer;
}
.active {
  background: gold;
}
</style>
