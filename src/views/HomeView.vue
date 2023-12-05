<template>
  <div class="h-100 d-flex flex-column">
    <Navbar />
    <div class="d-flex flex-grow-1 justify-content-center align-items-center">
      <div class="container py-2 py-md-0 py-lg-0">
        <!-- <div
          v-if="error === 'Invalid Credentials'"
          class="alert alert-info"
          role="alert"
        >
          A simple info alert—check it out!
        </div> -->
        <div class="w-100">
          <div class="card">
            <div class="card-body my-3 mx-2">
              <div
                class="row row-cols-1 row-cols-md-2 row-cols-lg-2 w-100 align-items-center"
              >
                <div class="col">
                  <img
                    src="../assets/svg/login-svg.svg"
                    class="px-3 mt-0 mt-md-3 mt-lg-3"
                    alt=""
                  />
                </div>
                <div class="col">
                  <form
                    class="card border-0"
                    id="login-card"
                    @submit.prevent="onSubmit"
                  >
                    <div class="card-body my-0 my-md-3 my-lg-3 mx-2">
                      <h5 class="h2 fw-bold mb-3 mb-md-5 mb-lg-5">Login</h5>
                      <div class="form-floating mb-4">
                        <input
                          type="email"
                          class="form-control"
                          v-model="email"
                          id="floatingInput"
                          placeholder="name@example.com"
                        />
                        <label for="floatingInput" class="form-label"
                          >Email address</label
                        >
                      </div>
                      <div class="form-floating mb-4">
                        <input
                          type="password"
                          class="form-control"
                          v-model="password"
                          id="floatingPassword"
                          placeholder="Password"
                        />
                        <label for="floatingPassword" class="form-label"
                          >Password</label
                        >
                      </div>
                      <div class="form d-flex align-items-center">
                        <div class="button">
                          <button class="btn px-3" type="submit">Login</button>
                        </div>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import loginImg from "../assets/svg/login-svg.svg";
export default {
  name: "LoginView",
  components: {
    Navbar,
  },

  data() {
    return {
      email: "",
      password: "",
      error: this.$store.getters.getErrors,
    };
  },
  methods: {
    async onSubmit() {
      if (this.email === "" || this.password === "") {
        debugger;
        this.$store.dispatch("catchError", "Invalid Credentials");
      } else {
        const isLogin = await this.$store.dispatch("login", {
          email: this.email,
          password: this.password,
        });
        isLogin
          ? await this.$router.push("/dashboard")
          : this.$store.dispatch("catchError", "User not found");
      }
    },
  },
};
</script>

<style scoped>
@media (min-width: 992px) {
  #login-card {
    max-width: 80%;
  }
}
.form-label {
  color: #1a202e;
}
.button .btn {
  color: white;
  background: #1a202e;
}
.button .btn:hover {
  color: #5c72a5;
}
.card {
  border: 1px solid #5c72a53f;
  background: #1e2535;
  color: white;
}
.flex-grow-1 {
  background: #1e2535;
}
.flex-column {
  animation: fadeIn 1s;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
.container,
.col {
  -webkit-transition: all 0.5s ease;
  -moz-transition: all 0.5s ease;
  -o-transition: all 0.5s ease;
  transition: all 0.5s ease;
}
</style>
