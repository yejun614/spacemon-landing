<template>
<div id="container" :class="{dark: isDarkmode}">
  <div id="profile-img"></div>

  <div id="introduce">
    <h1>Hello, I'm software engineer <em class="author">YeJun, Jung</em> in Republic of Korea.</h1>

    <div id="links">
      <light-button href="https://spacemon.cc" text="Tech Blog" :class="isDarkmode"></light-button>
      <primary-button href="https://github.com/yejun614" text="Github Profile" newTab="true"></primary-button>
    </div>
  </div>
</div>
</template>

<script>
import LightButton from '../button/LightButton.vue'
import PrimaryButton from '../button/PrimaryButton.vue'

export default {
  name: 'App',
  props: ['isDarkmode'],
  components: {
    LightButton,
    PrimaryButton
  }
}
</script>

<style scoped>
@keyframes FadeInAndDown {
  from {
    position: relative;
    bottom: 30px;

    opacity: 0;
  }

  to {
    position: relative;
    bottom: 0;
    
    opacity: 1;
  }
}

#container {
  display: flex;
  justify-content: center;
  align-items: center;
}

#profile-img {
  width: 270px;
  height: 270px;
  margin: 0 30px;

  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-image: url('https://avatars.githubusercontent.com/u/31740224?v=4');

  border-radius: 50%;

  position: relative;

  animation: FadeIn .3s forwards;
  transition: all .3s ease-in-out;
}

#profile-img:hover {
  transform: translate(0, -10px);
  box-shadow: 0 3px 4px #999;
}

#container.dark #profile-img:hover {
  transform: translate(0, -10px);
  box-shadow: 0 3px 4px black;
}

#introduce {
  width: 510px;
  height: 500px;

  display: flex;
  flex-direction: column;
  justify-content: center;
}

#introduce > * {
  opacity: 0;
}

h1 {
  font-size: 40px;

  margin: 20px;
  margin-bottom: 10px;

  animation: FadeInAndDown .7s forwards;
}

#container.dark h1 {
  color: #D9D9D9;
}

h1 em.author {
  color: coral;
  font-style: italic;
}

#container.dark h1 em.author {
  color: #9896D9;
}

#links {
  margin: 10px;
  display: flex;

  animation: FadeInAndDown .7s forwards .3s;
}

/* Mobile Screen */
@media screen and (max-width: 700px) {
  #container {
    flex-direction: column;
  }

  #profile-img {
    width: 120px;
    height: 120px;
  }

  #introduce {
    height: fit-content;
    align-items: center;
  }

  h1 {
    width: 80%;
    font-size: 30px;
    text-align: center;
  }
}

@media screen and (max-width: 600px) {
  h1 {
    width: 60%;
    font-size: 20px;
  }
  
  #links {
    flex-direction: column;
  }
}
</style>