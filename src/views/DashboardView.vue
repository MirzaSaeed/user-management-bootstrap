<template>
  <div class="dashboard">
    <!-- <nav class="navbar navbar-expand-lg">
      <div class="container-fluid">
        <router-link class="navbar-brand text-white mx-2" to="/"
          >Title</router-link
        >
        <div class="navbar-toggle">
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="d-flex nav mx-1">
              <-- <li class="nav-item m-1">
                <router-link class="text-decoration-none p-3" to="/"
                  >Login</router-link
                >
              </li> -->
    <!-- <li v-if="existUser?.id !== 1" class="nav-item m-1">
              <router-link class="text-decoration-none p-3" to="/"
                >Login</router-link
              >
            </li> -->
    <!-- <li class="nav-item m-1">
                <button
                  class="btn text-white text-decoration-none py-0"
                  @click="handleLogout"
                >
                  <span class="material-symbols-outlined"> logout </span>
                </button>
              </li>
            </ul>
          </div>
        </div>
      </div> -->
    <!-- </nav> -->
    <div id="wrapper">
      <!-- <Sidebar :tabs="tabs" :currentTab="currentTab" @tab="changeTab" /> -->
      <!-- <component :is="currentTabComponent" :key="currentTab"></component> -->
      <Sidebar />
      <router-view />
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";
import TabCreateUser from "@/components/UserForm.vue";
import TabUserList from "@/components/List.vue";
import Navbar from "../components/Navbar.vue";
export default {
  name: "DashboardView",
  components: {
    Sidebar,
    TabCreateUser,
    TabUserList,
    Navbar,
  },
  data() {
    return {
      // currentTab: "Create User",
      // tabs: "Create User,User List",
    };
  },
  methods: {
    // changeTab(tab) {
    //   this.currentTab = tab;
    // },
  },
  computed: {
    // currentTabComponent() {
    //   return "Tab" + this.currentTab.replace(" ", "");
    // },
  },
};
</script>

<style scoped>
#wrapper {
  padding-left: 0;
  -webkit-transition: all 0.5s ease;
  -moz-transition: all 0.5s ease;
  -o-transition: all 0.5s ease;
  transition: all 0.5s ease;
}

@media (min-width: 992px) {
  #wrapper {
    padding-left: 300px;
  }
}
.navbar-expand-lg {
  background: #1a202e;
}
nav div.container-fluid div ul.d-flex li a {
  color: white;
}
nav div.container-fluid div ul.d-flex li a.hover {
  color: #6373e5;
}
nav div.container-fluid div ul.d-flex li a.router-link-exact-active {
  color: #ffffff;
  border-bottom: 2px solid #6373e5;
}
.dashboard{
  animation: fadeIn 0.5s;
}
@keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
}
</style>
