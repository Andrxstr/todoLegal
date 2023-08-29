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
      <!-- <div v-if="isOpenMenu" :class="{ open: menu - options }">
        <div class="options" @click="redirectTo('opcion3')">Opción 3</div>
        <div class="options" @click="redirectTo('opcion1')">Opción 1</div>
        <div class="options" @click="redirectTo('opcion2')">Opción 2</div>
      </div> -->
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
    redirectTo(option) {
      // Realizar redireccionamiento interno aquí
      console.log(`Redireccionando a ${option}`);
    },
  },
};
</script>

<style scoped>

.navbar-left img.logo {
  /* margin-left: 20px; */
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

  /* .menu-options {
    position: absolute;
    top: 100%;
    right: 0;
    background-color: white;
    border: 1px solid #ccc;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 100;
    transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
    opacity: 0;
    visibility: hidden;
  }

  .menu-options.open {
    max-height: 500px;
    opacity: 1;
    visibility: visible;
  }

  .options {
    padding: 10px 20px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .options:hover {
    background-color: #e0e0e0;
  } */

}
</style>
