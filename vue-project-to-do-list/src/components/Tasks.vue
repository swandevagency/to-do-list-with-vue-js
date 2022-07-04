<template>
  <li>
    <div>
      <h3 v-if="!editText">{{ taskObject.t }}</h3>
      <p v-if="!editText">{{ taskObject.d }}</p>
      <form v-if="editText">
        <label for="taskEdit">Editing Task:</label>
        <input type="text" v-model="taskEdit" id="taskEdit" />
        <label for="descriptionEdit">Editing Description/Date:</label>
        <input type="text" v-model="descriptionEdit" id="descriptionEdit" />
        <div>
          <button type="button" @click="saveEdit">Save</button>
          <button type="button" @click="cancelEdit">Cancel</button>
        </div>
      </form>
    </div>
    <div class="svgs">
      <svg
        clip-rule="evenodd"
        fill-rule="evenodd"
        stroke-linejoin="round"
        stroke-miterlimit="2"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
        @click="removeFromList"
      >
        <path
          d="m12.002 2.005c5.518 0 9.998 4.48 9.998 9.997 0 5.518-4.48 9.998-9.998 9.998-5.517 0-9.997-4.48-9.997-9.998 0-5.517 4.48-9.997 9.997-9.997zm0 1.5c-4.69 0-8.497 3.807-8.497 8.497s3.807 8.498 8.497 8.498 8.498-3.808 8.498-8.498-3.808-8.497-8.498-8.497zm0 7.425 2.717-2.718c.146-.146.339-.219.531-.219.404 0 .75.325.75.75 0 .193-.073.384-.219.531l-2.717 2.717 2.727 2.728c.147.147.22.339.22.531 0 .427-.349.75-.75.75-.192 0-.384-.073-.53-.219l-2.729-2.728-2.728 2.728c-.146.146-.338.219-.53.219-.401 0-.751-.323-.751-.75 0-.192.073-.384.22-.531l2.728-2.728-2.722-2.722c-.146-.147-.219-.338-.219-.531 0-.425.346-.749.75-.749.192 0 .385.073.531.219z"
          fill-rule="nonzero"
        />
      </svg>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        @click="edit"
      >
        <path
          d="M18 14.45v6.55h-16v-12h6.743l1.978-2h-10.721v16h20v-10.573l-2 2.023zm1.473-10.615l1.707 1.707-9.281 9.378-2.23.472.512-2.169 9.292-9.388zm-.008-2.835l-11.104 11.216-1.361 5.784 5.898-1.248 11.103-11.218-4.536-4.534z"
        />
      </svg>
    </div>
  </li>
</template>

<script>
let arr = [];
export default {
  data() {
    return {
      editText: false,
      taskEdit: this.taskObject.t,
      descriptionEdit: this.taskObject.d,
    };
  },
  props: {
    taskObject: Object,
    tasks: Array,
  },
  methods: {
    removeFromList() {
      arr = this.tasks.filter((t) => t != this.taskObject);
      this.$emit('removeTask', arr);
    },
    edit() {
      this.editText = true;
    },
    saveEdit() {
      this.editText = false;
      if (this.taskEdit === '' || this.descriptionEdit === '')
        this.cancelEdit();
      else {
        this.taskObject.t = this.taskEdit;
        this.taskObject.d = this.descriptionEdit;
      }
    },
    cancelEdit() {
      this.editText = false;
      this.taskEdit = this.taskObject.t;
      this.descriptionEdit = this.taskObject.d;
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

form label {
  font-size: 14px;
  font-weight: 700;
}

form input {
  width: 100%;
  padding: 6px 14px;
  margin-top: 10px;
}

form button {
  width: 40%;
  margin-right: 10px;
}
.svgs {
  cursor: pointer;
}
</style>
