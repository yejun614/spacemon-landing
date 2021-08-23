<template>
<footer>
  <img src="../../assets/alien128.png" alt="logo" class="logo"/>
  <a href="#" class="link">spacemon.cc</a>
  <p>yejun614@naver.com</p>
  <p>Copyright 2021 YeJun, Jung All Right Reserved.</p>
</footer>
</template>

<script>
export default {

}
</script>

<style scoped>
footer {
  width: 100%;
  height: fit-content;

  background-color: black;
  padding: 20px 0;
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.logo {
  filter: invert(50%);
}

a {
  color: white;
  text-decoration: blink;
  border-bottom: 2px solid white;
  margin: 5px 0;
  margin-bottom: 30px;
}

p {
  color: coral;
  font-size: 12px;
  padding: 5px 0;
}
</style>
