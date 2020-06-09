<template>
  <div>
      <a v-for="l in linkList" :key="l.id">{{l}}</a>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <input :checked="todo.done" @change="toggle(todo)" type="checkbox" />
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
        <button @click="removeTodo(todo)">remove</button>
      </li>
      <li>
        <input @keyup.enter="addTodo" placeholder="What needs to be done?" />
      </li>
    </ul>
  </div>
</template>

<script>
import { mapMutations } from "vuex";

export default {
  asyncData(context) {
      
      console.log("CONTEXT", context.env)
    return {
      linkList: ["hello"]
    };
  },
  created(){
    //   console.log("APPNAME", process.env)
  },
  computed: {
    todos() {
         console.log("APPNAME 2", process.env.API_KEY)
      return this.$store.state.todosStore.list;
    }
  },
  methods: {
    addTodo(e) {
      this.$store.commit("todosStore/add", e.target.value);
      e.target.value = "";
    },
    ...mapMutations({
      toggle: "todosStore/toggle"
    }),
    removeTodo(todo) {
      this.$store.commit("todosStore/remove", todo);
    }
  }
};
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>