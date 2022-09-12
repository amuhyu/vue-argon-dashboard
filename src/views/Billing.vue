<template>
  <div class="card">
  <div class="card-header pb-0">
    <h6>Add User</h6>
  </div>
  <div class="card-body px-3 pt-0 pb-2">
    <div class="mb-3">
      <label for="example-text-input" class="form-control-label">Name</label>
      <input type="text" class="form-control" id="Name" v-model="name" />
    </div>
    <div class="mb-3">
      <label for="example-text-input" class="form-control-label">Email</label>
      <input type="text" class="form-control" id="Email" v-model="email" />
    </div>
    <button @click="post()" class="btn btn-primary">Add User</button>
    <div id="name"></div>
    <div id="email"></div>
  </div>
  </div>
<br>
  <div class="card">
  <div class="card-header pb-1">
    <h6>Delete User</h6>
  </div>
  <div class="card-body px-3 pt-0 pb-2">
    <button @click="deleteUser" class="btn btn-danger mt-3">Delete</button>
  </div>
</div>
</template>

<script>

import axios  from 'axios';
export default {
name: "addUser",
data() {
  return {
    get: []
  }
},
methods: {
  post(){
      axios.post("https://reqres.in/api/users?page=2", {
          name : this.name,
          email : this.email,
      })
      .catch((e) => {
          this.errors.push(e);
      });
      document.getElementById("name").innerHTML = '<div class="fs-6"> Name = '+ this.name +'</div>';
      document.getElementById("email").innerHTML = '<div class="fs-6"> Email = '+ this.email +'</div>';
  },
  async deleteUser() {
    let x = window.confirm("ARE YOU SURE DELETE THIS USER?");

    if (x) {
      const user = await axios.delete("https://reqres.in/api/users/2");

      console.log(user);
      alert("USER DELETED!");
    }
  }
}
};
</script>
