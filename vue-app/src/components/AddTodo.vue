<template>
  <div>
    <form @submit.prevent="addTodo">
      <input v-model="title" type="text" name="title" placeholder="请添加待办事项..." />
      <input type="submit" value="添加" class="btn" />
    </form>
  </div>
</template>

<script>
// import uuid from "uuid";
import axios from "axios";
export default {
  name: "AddTodo",
  mounted() {
    axios.get("http://jsonplaceholder.typicode.com/todos").then((res) => {
      this.today = res.data;
    });
  },
  data() {
    return {
      title: "",
      today: [],
    };
  },
  methods: {
    addTodo(e) {
      // e.preventDefault();
      // console.log(this.title);
      const newTodo = {
        // id: uuid.v4(),
        title: this.title,
        completed: false,
      };
      console.log(newTodo);
      // 注册事件
      this.$emit("handleAdd", newTodo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>
