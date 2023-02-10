<template>
  <div class="container">
    <h2 class="text-center mt-5">My Todo</h2>
    <input type="text" placeholder="Enter text" class="form-control" />
    <button class="btn btn-warning rounded-0">Submit</button>

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
            <div class="text-center">
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
</script>

<style scoped></style>
