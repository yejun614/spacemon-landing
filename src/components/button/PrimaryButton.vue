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
  color: #0074D9;
  font-size: 14px;
  font-weight: bold;
  text-decoration: blink;

  text-align: center;

  padding: 12px 20px;
  margin: 10px;

  background-color: transparent;
  border: 3px solid #0074D9;
  border-radius: 5px;

  transition: all .2s ease-in-out;
}

a:hover {
  color: white;
  background-color: #0074D9;
}
</style>