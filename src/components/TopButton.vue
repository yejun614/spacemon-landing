<template>
  <button 
    id="top-btn"
    :class="{dark : isDarkmode}"
    v-on:click="scrollTop()"
    v-if="isVisible"
  >Top</button>
</template>

<script>
export default {
  props: ['isDarkmode', 'active'],
  data: () => {
    return {
      isVisible: false
    }
  },
  methods: {
    scrollEventHandler () {
      const position = window.scrollY;
      const el = document.querySelector(this.active);

      if (position >= el.offsetTop) {
        this.isVisible = true;
      } else {
        this.isVisible = false;
      }
    },
    scrollTop () {
      scroll({
        top: 0,
        behavior: 'smooth'
      })
    }
  },
  mounted () {
    document.addEventListener('scroll', this.scrollEventHandler);
  }
}
</script>

<style scoped>
@keyframes FadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

#top-btn {
  position: fixed;
  right: 20px;
  bottom: 20px;

  padding: 10px 20px;

  color: black;
  font-size: 14px;
  font-weight: bold;
  text-transform: uppercase;

  background-color: white;
  border: 2px solid black;
  border-radius: 5px;

  transition: all .3s ease-in-out;
  animation: FadeIn .3s forwards;
  cursor: pointer;
}

#top-btn.dark {
  color: white;
  background-color: black;
  border-color: white;
}

#top-btn:hover {
  color: white;
  background-color: black;
}

#top-btn.dark:hover {
  color: black;
  background-color: white;
}
</style>