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
        <span class="todoContent"> 할 일을 등록하세요. </span>
      </li>
      <li class="todoList" v-for="(item, index) in todoList" :key="index">
        <span
          class="new"
          v-if="item.createdAt.getTime() + 1000 * 10 > new Date().getTime()"
          >new</span
        >
        <!-- 할 일 목록 -->
        <span class="todoContent" v-show="!item.edit">
          {{ item.content }}

          <!-- 
          10초후

          {{ item.createdAt.getSeconds() }}
          {{ item.createdAt.getSeconds() + 10 }}

          {{ item.createdAt.getTime() }} /
          {{ item.createdAt.getTime() + 1000 * 10 }} -->
          <!-- 
            1초는 1000 밀리초
            1분은 1000 * 60 = 60000밀리초
            1시간은 1000 * 60 * 60 = 3,600,000 밀리초
            1일은 1000 * 60 * 60 * 24 = 86,400,000 밀리초 -->
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
            v-show="item.edit"
            v-model="item.content"
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
export default {
  data() {
    return {
      todo: "",
      todoList: [],
      edit: false,
    };
  },
  methods: {
    addTodo() {
      if (!this.todo) {
        alert("할 일을 입력하세요");
      } else {
        this.todoList.push({ content: this.todo, createdAt: new Date() });
        this.todo = "";
      }
      this.$refs.todoInput.focus();

      // if (!this.todo) {
      //   alert("할 일을 입력하세요");
      //   this.$refs.todoInput.focus();
      //   return;
      // }
      // this.todoList.push({ content: this.todo, createdAt: new Date() });
      // this.todo = "";
    },

    removeTodo(i) {
      this.todoList.splice(i, 1);
    },

    editTodo(i) {
      this.todoList[i].edit = true;
    },

    saveTodo(i) {
      this.todoList[i].edit = false;
    },
  },
  created() {
    // map() 메서드 : 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환
    /*
      const array = [1, 4, 9, 16];
      const map = array.map(x => x * 2);
      console.log(map);

      // Expected output: Array [2, 8, 18, 32]
    */
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
