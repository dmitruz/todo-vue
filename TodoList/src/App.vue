<template>
  <div class="container" style="max-width: 600px">
    <h2 class="text-center mt-5">My Todo</h2>
    <div class="d-flex mt-5">
      <input v-model="task" type="text" placeholder="Enter text" class="w-100 form-control" />
      <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button>
    </div>

    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col" style="width: 120px">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="{ 'line-trhrough': task.status === 'finished' }">
              {{ task.name }}
            </span>
          </td>
          <td>
            <span
              class="pointer noselected"
              @click="changeStatus(index)"
              :class="{
                'text-danger': task.status === 'to-do',
                'text-success': task.status === 'finished',
                'text-warning': task.status === 'in-progress',
              }"
            >
              {{ capitalizeFirstChar(task.status) }}
            </span>
          </td>

          <td class="text-center">
            <div @click="deleteTask(index)">
              <span class="fa fa-trash pointer"></span>
            </div>
          </td>
          <td class="text-center">
            <div @click="editTask(index)">
              <p class="fa fa-pen pointer"></p>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
      data(){
       return {
       editedTask: 'null'
        statuses: ["to-do", "in-progress", "finished"],

         tasks: [

       {
            name: 'Learn Vue.js',
            status: 'to-do'
          },
       {
            name: 'Learn React.js',
            status: 'in-progress'
          },
           {
            name: "Create YouTube video.",
            status: "finished",
    },
         ]
       }
      }

      methods: {

       capitalizeFirstChar(str) {
       return str.charAt(0).toUpperCase() + str.slice(1);
      },

       changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
},
      deleteTask(index) {
  this.tasks.splice(index, 1);
},

editTask(index) {
  this.task = this.tasks[index].name;
  this.editedTask = index;
},

submitTask() {
  if (this.task.length === 0) return;

  if (this.editedTask != null) {
    this.tasks[this.editedTask].name = this.task;
    this.editedTask = null;
  } else {

    this.tasks.push({
      name: this.task,
      status: "todo",
    });
  }

  this.task = "";
},
},
};
</script>
<style scoped>
.pointer {
  cursor: pointer;
}
.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}
.line-through {
  text-decoration: line-through;
}
</style>
