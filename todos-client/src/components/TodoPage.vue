<template>
  <div class="container">
    <h2>Todo List</h2>
    <div class="input-group" style="margin-bottom:10px;">
      <input
        type="text"
        class="form-control"
        placeholder="할일을 입력하세요"
        v-model="name"
        v-on:keyup.enter="addTodo(name)"
      />
      <span class="input-group-btn">
        <button class="btn btn-default" type="button" @click="addTodo(name)">추가</button>
      </span>
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="(todo, index) in todos">
        {{index + 1 + '. '}}{{todo.name}}
        <div class="btn-group pull-right" style="font-size: 12px; line-height: 1;">
          <button
            type="button"
            class="btn-link dropdown-toggle"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            더보기
            <span class="caret"></span>
          </button>
          <ul class="dropdown-menu">
            <li>
              <a href="#" @click="deleteTodo(index)">삭제</a>
            </li>
          </ul>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoPage",
  data() {
    return {
      todos: [
        {
          name: "장 보기"
        },
        {
          name: "동기들 만나기"
        },
        {
          name: "vue js 공부하기"
        }
      ]
    };
  },
  methods: {
    deleteTodo(i) {
      this.todos.splice(i, 1);
    },
    addTodo(name) {
      if(name != null) {
        this.todos.push({name:name})
        this.name = null
      }
    }
  }
};
</script>
