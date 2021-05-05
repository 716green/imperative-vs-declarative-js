<template>
  <section>
    <h2>Declarative App</h2>
    <input type="text" v-model="taskInput" />
    <a @click="addNewTask" style="cursor: pointer">✅</a>
    <ul>
      <li
        v-for="(task, i) in tasks"
        :key="i"
        :class="task.completed ? 'item-style' : 'item-style__checked'"
      >
        <span>
          <strong @click="task.completed = !task.completed">
            {{ task.taskName }}
          </strong>
          <a @click="removeTask(i)">❌</a>
        </span>
      </li>
    </ul>
  </section>
</template>

<style>
  * {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 20px;
  }
  li {
    list-style: none;
  }
  .item-style {
    text-decoration: line-through;
  }
  .item-style__checked {
    text-decoration: none;
  }
</style>

<script>
  const appData = {
    data() {
      return {
        taskInput: '',
        tasks: [],
      };
    },
    methods: {
      addNewTask() {
        if (!this.taskInput) {
          alert('please add a task');
        } else {
          let newTask = {
            taskName: this.taskInput,
            completed: false,
          };
          this.tasks.push(newTask);
          this.taskInput = '';
        }
      },
      removeTask(i) {
        this.tasks.splice(i, 1);
      },
    },
  };
</script>
