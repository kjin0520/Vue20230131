<template>
  <div>
    <div class="inputBox">
      <!-- 할 일 입력 -->
      <input
        type="text"
        class="todoInput"
        placeholder="새로운 할 일을 입력하세요"
        autofocus
        ref="todoInput"
        v-model="todo"
      />
      <button class="todoBtn" @click="addTodo">등록</button>
    </div>
    <ul class="outputBox">
      <li class="todoList default" v-show="todoList.length === 0">
        <span class="todoContent">할 일을 등록하세요.</span>
      </li>
      <li class="todoList" v-for="(item, index) in todoList" :key="index">
        <span
          class="new"
          v-if="item.createdAt.getTime() + 1000 * 10 > new Date().getTime()"
          >new</span
        >
        <!-- 할 일 목록 -->
        <span class="todoContent" v-show="!item.edit">
          {{ item.todo }}
          <!-- {{ item.createdAt }} {{ item.edit }} -->
          <!-- {{ index }} -->
        </span>
        <span class="icons" v-show="!item.edit">
          <i class="xi-border-color rewrite" @click="editTodo(index)"></i>
          <i class="xi-trash delete" @click="removeTodo(index)"></i>
        </span>

        <!-- 할 일 수정 -->
        <span
          ><input
            type="text"
            class="todoEdit"
            ref="todoEdit"
            v-model="item.todo"
            v-show="item.edit"
        /></span>
        <span class="icons" v-show="item.edit">
          <i class="xi-check save" @click="saveTodo(index)"></i>
          <i class="xi-trash delete" @click="removeTodo(index)"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
class TodoItem {
  constructor(content) {
    this.todo = content;
    this.createdAt = new Date();
    this.edit = false;
  }
}

export default {
  data() {
    return {
      todo: "",
      todoList: [],
    };
  },
  methods: {
    addTodo() {
      if (!this.todo) {
        alert("할 일을 입력하세요");
        this.$refs.todoInput.focus();
        return;
      }
      this.todoList.push(new TodoItem(this.todo));
      this.todo = "";
    },

    removeTodo(i) {
      this.todoList.splice(i, 1);
      this.$refs.todoInput.focus();
    },

    editTodo(i) {
      this.todoList[i].edit = true;
    },

    saveTodo(i) {
      this.todoList[i].edit = false;
    },
  },
  created() {
    setInterval(() => {
      this.todoList = this.todoList.map((item) => item);
    }, 100);
  },
};
</script>

<style>
.inputBox {
  background-color: #eaeaea;
  padding: 30px;
  border-radius: 10px;
}
.outputBox {
  margin-top: 50px;
}
input,
button {
  border-radius: 5px;
  border: 1px solid #d1d1d1;
}

/* 할 일 입력 */
.todoInput {
  margin-right: 10px;
  padding: 5px;
  width: 80%;
}
.todoBtn {
  padding: 3.7px 10px;
}

/* 할 일 목록 */
.todoList.default {
  padding-left: 10px;
}
.todoList {
  border: 1px solid #eaeaea;
  border-radius: 5px;
  text-align: left;
  padding-left: 40px;
  margin: 10px 0;
  position: relative;
}
.todoContent {
  display: inline-block;
  padding: 5px;
  margin: 5px;

  overflow: hidden;
  width: auto;
  text-overflow: ellipsis;
}

/* 할 일 수정 */
.todoEdit {
  padding: 5px;
  margin: 7px;
  width: 80%;
}

/* new와 수정,삭제,완료 아이콘 */
.new {
  font-size: small;
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translate(0, -60%);
  background-color: yellow;
  color: orangered;
}
.icons {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translate(0, -50%);
}
.icons i {
  margin-left: 10px;
  cursor: pointer;
}
</style>
