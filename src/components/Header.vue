<template>
<header :class="{dark : isDarkmode}">
  <div id="logo-icon" class="item">
    <a href="#">
      <img src="../assets/alien128.png" alt="logo icon" />
    </a>
  </div>

  <div id="dark-btn" class="item">
    <DarkModeToggleButton v-on:change-mode="toggleDarkmode()" />
  </div>
</header>
</template>

<script>
import DarkModeToggleButton from './button/DarkModeToggleButton.vue'

export default {
  name: 'Header',
  components: {
    DarkModeToggleButton,
  },
  data: () => {
    return {
      isDarkmode: false,
    }
  },
  methods: {
    toggleDarkmode () {
      this.isDarkmode = !this.isDarkmode;
      this.$emit('change-mode');
    }
  }
}
</script>

<style scoped>
header {
  width: 100%;
  height: 50px;
  padding: 25px 0;

  position: fixed;
  top: 0;
  left: 0;

  display: flex;
  justify-content: space-between;
  align-items: center;

  transition: all .3s ease-in-out;
}

header > .item {
  margin: 0 50px;
}

#logo-icon img {
  width: 65px;
  height: 65px;
}

header.dark #logo-icon img {
  filter: invert(50%);
}

@media screen and (max-width: 700px) {
  header > .item {
    margin: 0 20px;
  }
}
</style>