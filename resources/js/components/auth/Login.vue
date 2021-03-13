<template>
  <div>
    <h3>Login</h3>
    <form @submit.prevent="authenticate">
      <label>Email</label>
      <input type="email" v-model="form.email" />
      <label>Password</label>
      <input type="password" v-model="form.password" />
      <input type="submit" value="Login" />
      <div class="form-group row" v-if="authError">
        <p class="error">
          {{ authError }}
        </p>
      </div>
    </form>
  </div>
</template>

<script>
import { login } from "../../helpers/auth";

export default {
  name: "login",
  data() {
    return {
      form: {
        email: "jhon@doe.com",
        password: "",
      },
      error: null,
    };
  },
  methods: {
    authenticate() {
      this.$store.dispatch("login");

      login(this.$data.form)
        .then((response) => {
          this.$store.commit("loginSuccess", response);
          this.$router.push({ path: "/" });
        })
        .catch((error) => {
          this.$store.commit("loginFailed", error);
        });
    },
  },
  computed: {
    authError() {
      return this.$store.getters.authError;
    },
  },
};
</script>

<style scoped>
.error {
    text-align: center;
    color: red;
}
</style>