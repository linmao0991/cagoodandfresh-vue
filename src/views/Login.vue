<template>
  <div class="container">
    <div
      class="justify-content-md-center row"
      style="margin-top: 40px; margin-bottom: 20px"
    >
      <div class="col-md-5"><h1 style="text-align: center">Log In</h1></div>
    </div>
    <div class="justify-content-md-center row">
      <div
        class="col-md-5"
        style="
          background-color: rgb(44, 44, 44);
          border-radius: 15px;
          padding: 30px;
        "
      >
        <div
          id="failed-login"
          style="
            width: 100%;
            max-height: 0;
            overflow: hidden;
            opacity: 0;
            transition-property: max-height, opacity;
            transition-duration: 1s;
          "
        >
          <div role="alert" class="fade alert alert-danger show">
            <p style="margin: 0; text-align: center"></p>
            <p style="margin: 0; text-align: center">Error:</p>
          </div>
        </div>
        <form style="align-content: center" v-on:submit.prevent="login($event)">
          <label>Email</label>
          <input id="email" type="email" autocomplete="email" />
          <br />
          <label>Password</label>
          <input
            id="password"
            type="password"
            autocomplete="current-password"
          />
          <br />
          <input type="submit" value="Login" />
          <button type="button">Sign Up</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {};
  },
  methods: {
    async login(event) {
      console.log(event.target.email.value);
      console.log(event.target.password.value);
      const res = await fetch("http://localhost:3001/api/login", {
        method: "POST",
        headers: {
          "Content-Type": "application/json;charset=UTF-8",
        },
        body: JSON.stringify({
          email: event.target.email.value,
          password: event.target.password.value,
        }),
      });
      console.log(res);
    },
  },
};
</script>

<style scoped></style>
