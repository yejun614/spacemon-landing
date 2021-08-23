<template>
  <button v-on:click="toggle()" id="dark-toggle" :class="mode">
    <div class="back"></div>
    <div class="front"></div>
  </button>
</template>

<script>
export default {
  data: () => {
    return {
      mode: 'light',
    }
  },
  methods: {
    toggle () {
      // Toggle Mode.
      if (this.mode == 'light') {
        this.mode = 'dark';
      } else {
        this.mode = 'light';
      }

      // Raise Event.
      this.$emit('change-mode', this.mode);
    }
  }
}
</script>

<style scoped>
@keyframes ToMoon {
  from { transform: translate(-40px, 40px); }
  to { transform: translate(-7px, 7px); }
}

@keyframes ToSun {
  from { transform: translate(-7px, 7px); }
  30% { transform: translate(-7px, 7px); }
  to { transform: translate(-40px, 40px); }
}

#dark-toggle {
  width: 40px;
  height: 40px;

  border: 3px solid black;
  border-radius: 50%;

  background-color: white;
  overflow: hidden;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  position: relative;
  cursor: pointer;
}

#dark-toggle > div {
  width: 30px;
  height: 30px;
  border-radius: 50%;
}

#dark-toggle, #dark-toggle > div {
  transition: all .3s ease-in-out;
}

#dark-toggle .back {
  background-color: black;
}

#dark-toggle .front {
  background-color: white;
  position: absolute;
}

#dark-toggle.dark {
  border: 3px solid white;
  background-color: black;
}

#dark-toggle.dark .back {
  background-color: white;
}

#dark-toggle.dark .front {
  background-color: black;
  position: absolute;
}

#dark-toggle.light .front {
  transform: translate(-7px, 7px);
}

#dark-toggle.dark .front {
  transform: translate(-40px, 40px);
}

#dark-toggle.light:hover .front {
  animation: ToMoon .5s forwards;
}

#dark-toggle.dark:hover .front {
  animation: ToSun 1s forwards;
}
</style>
