<template>
  <a :href="href" :target="target">{{ text }}</a>
</template>

<script>
export default {
  props: ['href', 'text', 'newTab'],
  data: () => {
    return {
      target: '_self'
    }
  },
  mounted () {
    this.target = this.newTab ? '_blank' : '_self';
  }
}
</script>

<style scoped>
a {
  width: fit-content;

  color: coral;
  font-size: 14px;
  font-weight: bold;
  text-decoration: blink;

  text-align: center;

  padding: 5px 15px;
  margin: 10px;
  border-radius: 5px;

  background-color: transparent;

  transition: all .2s ease-in-out;
}

a:hover {
  color: white;
  background-color: coral;
}
</style>
