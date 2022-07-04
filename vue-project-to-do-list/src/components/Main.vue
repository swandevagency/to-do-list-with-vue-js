<template>
  <div>
    <form @submit.prevent="addToList()" id="add-task-form">
      <label for="task">Task</label>
      <input v-model="task" type="text" id="task" />
      <label for="description">Description or Date</label>
      <input v-model="des" type="text" id="description" />
      <button v-if="task && des">Add To List</button>
    </form>
    <div id="cards">
      <ul>
        <Tasks
          v-for="singleTask in tasks"
          :key="singleTask.id"
          :task-object="singleTask"
          :tasks="tasks"
          @removeTask="removeFrom"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import Tasks from './Tasks.vue';

let id = 0;
export default {
  data() {
    return {
      task: '',
      des: '',
      tasks: [],
    };
  },
  methods: {
    addToList() {
      this.tasks.push({ id: id++, t: this.task, d: this.des });
    },
    removeFrom(value) {
      this.tasks = value;
    },
  },
  components: {
    Tasks,
  },
};
</script>

<style>
#add-task-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 50px;
}

#add-task-form label {
  text-align: left;
  margin-bottom: 6px;
}

input {
  width: 40%;
  padding: 10px 20px;
  border: 1px solid rgb(194, 194, 194);
  border-radius: 6px;
  margin-bottom: 20px;
}

input:hover {
  border: 1px solid rgb(184, 184, 184);
}

input:focus-visible {
  border: 1px solid rgb(184, 184, 184);
}

button {
  width: 22%;
  padding: 10px 15px;
  background-color: black;
  color: white;
  cursor: pointer;
  border-radius: 6px;
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.2);
  margin-top: 20px;
}

button:hover {
  background-color: rgb(80, 80, 80);
}

ul {
  width: 50%;
  margin: 50px auto;
  list-style-type: none;
  display: flex;
  align-items: flex-end;
  flex-wrap: wrap;
}

ul li {
  width: 100%;
  text-align: left;
  background-color: rgb(211, 211, 211);
  border-radius: 6px;
  box-shadow: -2px 7px 16px rgba(0, 0, 0, 0.2);
  padding: 15px 30px;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

ul li h3 {
  margin-bottom: 4px;
}

ul li p {
  font-size: 14px;
}

ul li svg {
  width: 16px;
  height: 16px;
}

.svgs {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
