<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 mt-5 mx-auto">
        <form v-on:submit.prevent="register">
          <h1 class="h3 mb-3 font-weight-normal">Register</h1>
          <div class="form-group">
            <label for="name">Nama</label>
            <input
              type="name"
              v.model="name"
              class="form-control"
              name="name"
              placeholder="Enter name.."
            />
          </div>
          <div class="form-group">
            <label for="email">Email Address</label>
            <input
              type="email"
              v.model="email"
              class="form-control"
              name="email"
              placeholder="Enter email.."
            />
          </div>
          <div class="form-group">
            <label for="email">Password</label>
            <input
              type="email"
              v.model="password"
              class="form-control"
              name="password"
              placeholder="Enter password.."
            />
          </div>
          <button class="btn btn-lg btn-primary btn-block">Sign in</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import router from "../router"

export default {
  data() {
    return {
        name: "",
      email: "",
      password: ""
    };
  },
  methods: {
    register() {
      axios
        .post("/api/register", {
            name: this.name,
          email: this.email,
          password: this.password
        })
        .then((res) => {
          console.log(res)
          router.push({ name: 'login' });
        })
        .catch((err) => {
          console.log(err);
        })
    }
  }
};
</script>