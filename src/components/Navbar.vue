<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <span class="navbar-brand text-white mx-2">Welcome</span>

      <ul class="d-flex nav mx-1">
        <li class="nav-item m-1">
          <router-link class="text-decoration-none p-3" to="/"
            >Login</router-link
          >
        </li>
        <!-- <li v-if="existUser?.id !== 1" class="nav-item m-1">
              <router-link class="text-decoration-none p-3" to="/"
                >Login</router-link
              >
            </li> -->
        <!-- <li v-else-if="existUser?.id === 1" class="nav-item m-1">
              <button
                class="btn text-white text-decoration-none py-0"
                @click="handleLogout"
              >
                <span class="material-symbols-outlined"> logout </span>
              </button>
            </li> -->
      </ul>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style scoped>
.navbar-expand-lg {
  background: #1a202e;
}
nav div.container-fluid ul.d-flex li a {
  color: white;
}
nav div.container-fluid ul.d-flex li a.hover {
  color: #6373e5;
}
nav div.container-fluid ul.d-flex li a.router-link-exact-active {
  color: #ffffff;
  border-bottom: 2px solid #6373e5;
}
</style>
