<template>
  <div class="card">
    <div class="card-header pb-0">
      <h6>Update User</h6>
    </div>
    <div class="card-body px-3 pt-0 pb-2">
      <div class="mb-3">
        <label for="example-text-input" class="form-control-label">Name</label>
        <input type="text" class="form-control" id="Name" v-model="name" />
      </div>
      <div class="mb-3">
        <label for="example-text-input" class="form-control-label">Job</label>
        <input type="text" class="form-control" id="Email" v-model="email" />
      </div>
      <button @click="update()" class="btn btn-primary">Update</button>
      <div id="name"></div>
      <div id="job"></div>
    </div>
  </div>
</template>

<script>

import axios from 'axios';
export default {
  name: "updatUser",
  data() {
    return {
      get: []
    }
  },
  methods: {
    async update() {
      try {
        const user = await axios.put("https://reqres.in/api/users/2", {
          name: this.name,
          job: this.job,
        });
        console.log(user);
        alert("Data Updated!!");
      } catch (e) {
        console.log(e);
      }
    }
  },
}
</script>
