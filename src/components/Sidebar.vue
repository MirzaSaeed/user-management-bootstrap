<template>
  <div id="sidebar-wrapper">
    <aside id="sidebar">
      <ul id="sidemenu" class="sidebar-nav">
        <!-- <li
          v-for="tab in tabs.split(',')"
          :key="tab"
          :class="['tab-button', { active: currentTab === tab }]"
          @click="changeTab(tab)"
        >
          <span class="sidebar-title">{{ tab }}</span>
        </li> -->
        <li id="nav-heading" class="border-bottom border-secondary">
          <span class="navbar-brand text-white mx-2 text-decoration-none w-100"
            >Title</span
          >
        </li>
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
    </aside>
  </div>
</template>

<script>
export default {
  props: {
    tabs: String,
    currentTab: String,
  },
  methods: {
    // changeTab(tab) {
    //   this.$emit("tab", tab); //passing prop to parent component i.e., Dashboard
    // },
  },
};
</script>

<style scoped>
@media (min-width: 992px) {
  #sidebar-wrapper {
    width: 300px;
  }
}

#sidebar-wrapper {
  z-index: 1000;
  position: fixed;
  left: 225px;
  width: 300px;
  height: 100%;
  margin-left: -225px;
  /* overflow-y: auto; */
  background: #1a202e;
  -webkit-transition: all 0.5s ease;
  -moz-transition: all 0.5s ease;
  -o-transition: all 0.5s ease;
  transition: all 0.5s ease;
}

#sidebar-wrapper .sidebar-nav {
  position: absolute;
  top: 0;
  width: 300px;
  font-size: 14px;
  margin: 0;
  padding: 0;
  list-style: none;
}

#sidebar-wrapper .sidebar-nav li {
  text-indent: 0;
  line-height: 45px;
}
#sidebar-wrapper .sidebar-nav li#nav-heading {
  font-size: 20px;
  font-weight: bold;
  padding-left: 15px;
}

#sidebar-wrapper .sidebar-nav li.sidebar-list .sidebar-title {
  font-size: 16px;
  padding: 0 2px;
  display: inline-block;
  text-indent: 15px;
}

@media (max-width: 992px) {
  #sidebar-wrapper {
    display: none;
  }
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
.sidebar-list {
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
</style>
