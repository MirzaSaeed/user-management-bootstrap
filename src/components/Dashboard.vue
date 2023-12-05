<template>
  <div class="card border-0">
    <nav
      aria-label="breadcrumb"
      class="border-bottom border-secondary navbar-title"
    >
      <ol class="breadcrumb mb-0">
        <li
          id="sidebar-menu-button"
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
          Dashboard
        </li>
      </ol>
      <button
        class="btn text-white text-decoration-none pt-0 pt-md-2 pt-lg-2 pb-0"
        @click="handleLogout"
      >
        <span class="material-symbols-outlined"> logout </span>
      </button>
    </nav>
    <div class="card-body pt-0">
      <div class="d-flex flex-grow-1 justify-content-center align-items-center">
        <div class="row row-cols-1 row-cols-md-1 row-cols-lg-1 w-50">
          <div class="col d-flex justify-content-center">
            <img src="../assets/svg/dashboard.svg" class="w-100" alt="" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async handleLogout() {
      await this.$store.dispatch("logout");
      this.$router.push("/");
    },
  },
};
</script>

<style scoped>
@media (min-width: 992px) {
  #sidebar-menu,
  #sidebar-menu-button {
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
</style>
