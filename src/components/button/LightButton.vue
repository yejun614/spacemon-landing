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
  color: coral;
  font-size: 14px;
  font-weight: bold;
  text-decoration: blink;

  text-align: center;

  padding: 12px 20px;
  margin: 10px;

  background-color: transparent;
  border: 3px solid coral;
  border-radius: 5px;

  transition: all .2s ease-in-out;
}

a:hover {
  color: white;
  background-color: coral;
}
</style>