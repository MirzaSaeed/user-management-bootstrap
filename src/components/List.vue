<template>
  <div class="card border-0">
    <nav
      aria-label="breadcrumb"
      class="border-bottom border-secondary navbar-title"
      id="nav-bar-list"
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
          class="breadcrumb-item active text-white ps-3 pt-2 fw-bold"
          aria-current="page"
        >
          User List
        </li>
      </ol>

      <button
        class="btn text-white text-decoration-none pt-0 pt-md-2 pt-lg-2 pb-0"
        @click="handleLogout"
      >
        <span class="material-symbols-outlined"> logout </span>
      </button>
    </nav>
    <div class="card-body pt-0 dashboard-list">
      <div
        v-if="this.$store.getters.getUsers.length === 0"
        class="d-flex flex-grow-1 justify-content-center align-items-center"
        id="no-data"
      >
        <div class="row row-cols-1 row-cols-md-1 row-cols-lg-1 w-50">
          <div
            class="col d-flex justify-content-center flex-column align-items-center"
          >
            <p class="h1 text-white mt-3 fw-normal">No User Exist</p>
            <img src="../assets/svg/no-list.svg" class="w-100" alt="" />
          </div>
        </div>
      </div>
      <div
        v-else-if="'this.$store.getters.getUsers.length > 0'"
        class="table-responsive"
      >
        <table class="table table-hover my-3">
          <thead>
            <tr class="table-head">
              <th scope="col" class="table-row">Id</th>
              <th scope="col" class="table-row">First</th>
              <th scope="col" class="table-row">Last</th>
              <th scope="col" class="table-row">Email</th>
              <th scope="col" class="table-row">Age</th>
              <th scope="col" class="table-row">Job Title</th>
              <th scope="col" class="table-row">Country</th>
              <th scope="col" class="table-row">Action</th>
            </tr>
          </thead>
          <tbody>
            <tr
              class="table-body"
              v-for="(user, index) in users"
              :key="user.id"
            >
              <th scope="row" class="table-row">{{ index + 1 }}</th>
              <td class="table-row">{{ user.firstName }}</td>
              <td class="table-row">{{ user.lastName }}</td>
              <td class="table-row">{{ user.email }}</td>
              <td class="table-row">{{ user.age }}</td>
              <td class="table-row">{{ user.jobTitle }}</td>
              <td class="table-row">{{ user.country }}</td>
              <td class="table-row px-0">
                <button class="btn list-button btn-sm text-info me-1">
                  Edit</button
                ><button
                  class="btn list-button btn-sm text-danger"
                  @click="deleteUser(user.id)"
                >
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: this.$store.getters.getUsers,
    };
  },
  methods: {
    async handleLogout() {
      await this.$store.dispatch("logout");
      this.$router.push("/");
    },

    async deleteUser(id) {
      await this.$store.dispatch("deleteUser", id);
      this.$store.getters.getUsers;
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
.list-button {
  background: none !important;
}
.list-button:hover {
  background: #1a202e !important;
}
.table-head .table-row {
  background: #1a202e;
  color: white;
}
.table-body .table-row {
  background: #293247;
  color: white;
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

.offcanvas-start,
#no-data {
  transition: all ease-in-out 0.5s;
  animation: fadeIn 1s;
}
.dashboard-list {
  animation: fadeIn 1s;
  overflow: auto;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
#nav-bar-list {
  position: sticky;
  top: 0;
}
</style>
