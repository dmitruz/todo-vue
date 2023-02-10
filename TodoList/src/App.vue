<template>
  <div class="container">
    <h2 class="text-center mt-5">My Todo</h2>
    <input v-model="task" type="text" placeholder="Enter text" class="form-control" />
    <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button>

    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>Learn Vue.js</td>
          <td>{{ task.name }}</td>
          <td>{{ task.status }}</td>
          <div class="text-center">
            <span class="fa fa-pen"></span>
          </div>

          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-pen"></span>
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
 task: '',
   tasks: [

 {
      name: 'Learn Vue.js',
      status: 'to-do'
    },
 {
      name: 'Learn React.js',
      status: 'in-progress'
    },
   ]
 }
}

methods: {
  submitTask() {
    if (this.task.length === 0) return;

    this.tasks.push({
    name: this.task,
    status: 'to-do'
    });

    this.task = '';
    }


  deleteTask(index) {
    this.tasks.splice(index, 1);
    }
  }
}
</script>

<style scoped></style>
