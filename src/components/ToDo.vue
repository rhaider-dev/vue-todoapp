<template>
  <div>
    <h1>To Do App</h1>
    <br />
    <input type="text" id="toDoValue" v-model="toDoValue" />
    <button @click="addToDo" class="btn btn-primary ml-2">Add To Do</button>

    <div class="card mt-3">
      <p v-if="toDoList.length==0" class="d-flex justify-content-center m-2">No list yet</p>
      <ol>
        <li v-for="(item,i) in toDoList" :key="`${i}-${item}`" class="m-2">
          <span v-show="item.seen" v-if="!item.check">{{item.name}}</span>
          <span v-show="item.check">
            <del>{{item.name}}</del>
          </span>
          <span v-show="!item.seen">
            <input type="text" v-model="item.name" />
          </span>

          <button @click="removeToDo(i)" v-show="item.seen" class="btn btn-danger ml-2">Remove</button>
          <button @click="editToDo(item)" v-show="item.seen" class="btn btn-warning ml-2">Edit</button>
          <button @click="checkToDo(item)" v-show="item.seen" class="btn btn-success ml-2">Check</button>
          <button @click="saveToDo(item)" v-show="!item.seen" class="btn btn-success ml-2">Save</button>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",

  data: function () {
    return {
      toDoList: [],
      toDoValue: "",
    };
  },
  methods: {
    addToDo: function () {
      if (this.toDoValue == "") {
        alert("Put some value!");
        return;
      }

      this.toDoList.push({
        name: this.toDoValue,
        seen: true,
        check: false,
      });
      this.showEdit = true;
      this.toDoValue = "";
    },
    removeToDo: function (index) {
      this.toDoList.splice(index, 1);
    },
    editToDo: function (item) {
      item.seen = !item.seen;
    },
    checkToDo: function (item) {
      item.check = !item.check;
    },
    saveToDo: function (item) {
      if (item.name == "") {
        alert("Put some value!");
        return;
      }
      item.seen = !item.seen;
    },
  },
};
</script>

