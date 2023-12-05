<template>
  <div>
    <UserForm />
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";
import UserForm from "@/components/UserForm.vue";
export default {
  name: "CreateUserView",
  components: {
    Sidebar,
    UserForm,
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
</style>
