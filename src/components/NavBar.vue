<template>
  <nav class="navbar">
    <div class="navbar-left">
      <img class="logo" src="../assets/logo_todolegal.png" />
    </div>
    <div class="navbar-right">
      <img
        v-if="showImageDesktop"
        class="desktop-image"
        src="../assets/smart_Contracts_Suite.png"
        alt="Desktop Image"
      />
      <div class="menu" @click="toggleMenu">
        <div class="menu-line" v-for="line in 3" :key="line"></div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      showImageDesktop: true,
      isOpenMenu: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isOpenMenu = !this.isOpenMenu;
    },
  },
};
</script>

<style scoped>

.navbar-left img.logo {
  width: 180px;
  height: 50px;
  padding: 3px;
}

.navbar-right {
  display: flex;
  align-items: center;
}

.navbar-right img.desktop-image {
  max-height: 120px;
  margin-right: 20px;
}

.menu {
  flex-direction: column;
  cursor: pointer;
  margin-right: 20px;
}

.menu .menu-line {
  width: 30px;
  height: 3px;
  margin: 4px 0;
  background-color: blue;
  border-radius: 10px;
}

@media (max-width: 768px) {
  .navbar-right img.desktop-image {
    display: none;
  }

  .navbar-left img.logo {
  width: 180px;
  height: 50px;
}

}
</style>
