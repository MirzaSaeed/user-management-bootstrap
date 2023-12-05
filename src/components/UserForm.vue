<template>
  <div class="card border-0">
    <nav
      aria-label="breadcrumb"
      class="border-bottom border-secondary navbar-title"
    >
      <ol class="breadcrumb mb-0">
        <li
          id="sidebar-menu"
          class="breadcrumb-item active text-white ps-3 pt-2 fw-bold"
          aria-current="page"
        >
          <button
            class="btn btn-sm pt-0"
            type="button"
            data-bs-toggle="offcanvas"
            data-bs-target="#sidebar-menu-list"
            aria-controls="offcanvasExample"
          >
            <span class="material-symbols-outlined"> menu </span>
          </button>

          <div
            class="offcanvas offcanvas-start"
            tabindex="-1"
            id="sidebar-menu-list"
            aria-labelledby="offcanvasExampleLabel"
          >
            <div class="offcanvas-header border-bottom">
              <h5 class="offcanvas-title" id="offcanvasExampleLabel">Menu</h5>
              <button
                type="button"
                class="btn"
                data-bs-dismiss="offcanvas"
                aria-label="Close"
              >
                <span class="material-symbols-outlined"> close </span>
              </button>
            </div>
            <div class="offcanvas-body px-0">
              <ul id="sidemenu" class="sidebar-nav">
                <li class="sidebar-list">
                  <router-link
                    class="sidebar-title text-decoration-none w-100"
                    to="/dashboard/create-user"
                    >Create User</router-link
                  >
                </li>
                <li class="sidebar-list">
                  <router-link
                    class="sidebar-title text-decoration-none w-100"
                    to="/dashboard/user-list"
                    >User List</router-link
                  >
                </li>
              </ul>
            </div>
          </div>
        </li>
        <li
          class="breadcrumb-item active text-white ps-2 pt-2 fw-bold"
          aria-current="page"
        >
          Create User
        </li>
      </ol>
      <button
        class="btn text-white text-decoration-none pt-0 pt-md-2 pt-lg-2 pb-0"
        @click="handleLogout"
      >
        <span class="material-symbols-outlined"> logout </span>
      </button>
    </nav>
    <form class="card-body pt-0 dashboard-form" @submit.prevent="onSubmit">
      <h5 class="h4 fw-normal my-3 text-white">Register Users</h5>
      <div class="row">
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-2">
          <div class="col">
            <div class="row">
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="text"
                    class="form-control"
                    v-model="firstName"
                    id="floatingInput"
                    placeholder="..."
                  />
                  <label for="floatingInput" class="form-label"
                    >First Name</label
                  >
                </div>
              </div>
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="text"
                    class="form-control"
                    v-model="lastName"
                    id="floatinglastName"
                    placeholder="..."
                  />
                  <label for="floatinglastName" class="form-label"
                    >Last Name</label
                  >
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="email"
                    class="form-control"
                    v-model="email"
                    placeholder="..."
                    id="floatingInput"
                  />
                  <label for="floatingInput" class="form-label"
                    >Email address</label
                  >
                </div>
              </div>
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="number"
                    class="form-control"
                    v-model="age"
                    placeholder="..."
                    id="floatingage"
                  />
                  <label for="floatingPassword" class="form-label">Age</label>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="text"
                    class="form-control"
                    v-model="jobTitle"
                    id="floatingInput"
                    placeholder="...."
                  />
                  <label for="floatingInput" class="form-label"
                    >Job Title</label
                  >
                </div>
              </div>
              <div class="col-6">
                <div class="form-floating mb-4">
                  <input
                    type="text"
                    class="form-control"
                    v-model="country"
                    id="floatingCountry"
                    placeholder="..."
                  />
                  <label for="floatingCountry" class="form-label"
                    >Country</label
                  >
                </div>
              </div>
              <div class="form d-flex align-items-center">
                <div class="button">
                  <button class="btn px-3" type="submit">Create User</button>
                </div>
              </div>
            </div>
          </div>
          <div class="col d-flex justify-content-center">
            <img src="../assets/svg/form.svg" class="w-75" alt="" />
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      age: "",
      jobTitle: "",
      country: "",
    };
  },
  methods: {
    async handleLogout() {
      await this.$store.dispatch("logout");
      this.$router.push("/");
    },
    onSubmit() {
      try {
        if (
          this.firstName === "" ||
          this.lastName === "" ||
          this.email === "" ||
          this.age === "" ||
          this.jobTitle === "" ||
          this.country === ""
        ) {
          alert("fill all the fields");
        } else {
          if (this.$store.state.users.length === 0) {
            this.$store.dispatch("addUser", {
              id: this.$store.state.users.length + 1,
              firstName: this.firstName,
              lastName: this.lastName,
              email: this.email,
              age: this.age,
              jobTitle: this.jobTitle,
              country: this.country,
              createdAt: new Date(),
              updatedAt: null,
            });
            this.firstName = "";
            this.lastName = "";
            this.email = "";
            this.age = "";
            this.jobTitle = "";
            this.country = "";
            this.$store.getters.getUsers;
          } else if (this.$store.state.users.length > 0) {
            let existEmail;
            const isExist = this.$store.state.users.filter((user) => {
              if (user.email === this.email) {
                existEmail = user.email;
              }
            });
            if (existEmail === this.email) {
              alert("User already exists");
            } else {
              const usersClone = JSON.parse(
                JSON.stringify(this.$store.state.users)
              );
              usersClone.sort((a, b) => b.id - a.id);
              this.$store.dispatch("addUser", {
                id: usersClone[0].id + 1,
                firstName: this.firstName,
                lastName: this.lastName,
                email: this.email,
                age: this.age,
                jobTitle: this.jobTitle,
                country: this.country,
                createdAt: new Date(),
                updatedAt: null,
              });

              this.firstName = "";
              this.lastName = "";
              this.email = "";
              this.age = "";
              this.jobTitle = "";
              this.country = "";
            }
          }
        }
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
@media (min-width: 992px) {
  #sidebar-menu {
    display: none;
  }
}

.card {
  background: #232b3e;
}
.form-label {
  color: #1a202e;
}
.btn,
.btn-close,
.offcanvas {
  color: white;
  background: #1a202e;
}

.btn-close,
.btn:hover {
  color: #5c72a5;
}
.navbar-title {
  background: #1a202e;
  padding: 4px 0 0;
  display: flex;
  justify-content: space-between;
}

/* sidebar css */
.sidebar-nav {
  /* font-size: 14px; */
  list-style: none;
  padding-left: 0;
}

.sidebar-nav li {
  text-indent: 0;
  line-height: 45px;
}

.sidebar-nav li.sidebar-list .sidebar-title {
  font-size: 16px;
  padding: 0 2px;
  font-weight: 400;
  display: inline-block;
  text-indent: 15px;
}

.sidebar-nav li {
  color: #fff !important;
}
.sidebar-nav li.sidebar-list:hover {
  background: #131822 !important;
  color: #6373e5 !important;
  padding-left: 5px;
  transition: all ease-in-out 0.5s;
}
.sidebar-nav li.sidebar-list:hover a {
  background: #131822 !important;
  color: #6373e5 !important;
  padding-left: 5px;
  transition: all ease-in-out 0.5s;
}
.sidebar-nav li.sidebar-list a:hover {
  cursor: pointer;
  background: #131822 !important;
  color: #6373e5 !important;
  padding-left: 5px;
  transition: all ease-in-out 0.5s;
}
.sidebar-nav li.sidebar-list a {
  color: #fff !important;
}

.sidebar-nav li.sidebar-list a.router-link-exact-active {
  color: #6373e5 !important;
  background: #131822 !important;
  padding-left: 5px;
  transition: all ease-in-out 0.5s;
}

.offcanvas-start {
  transition: all ease-in-out 0.5s;
  animation: fadeIn 1s;
}

.dashboard-form {
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
.col {
  -webkit-transition: all 0.5s ease;
  -moz-transition: all 0.5s ease;
  -o-transition: all 0.5s ease;
  transition: all 0.5s ease;
}
</style>
