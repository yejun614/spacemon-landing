<template>
  <h2 :class="{dark: isDarkmode}">Do you have a question to me?</h2>
  <light-button href="#" text="Contact Me" />
</template>

<script>
import LightButton from '../button/LightButton.vue'

export default {
  props: ['isDarkmode'],
  components: {
    LightButton,
  }
}
</script>

<style scoped>
h2 {
  font-size: 30px;
  font-weight: normal;
  font-family: 'Staatliches', cursive;
  margin: 40px;
}

h2.dark {
  color: white;
}

@media screen and (max-width: 700px) {
  h2 {
    font-size: 20px;
  }
}
</style>