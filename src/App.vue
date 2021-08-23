<template>
<main :class="{ dark: isDarkmode }" ref="main">  
  <section id="intro">
    <intro-view :isDarkmode="isDarkmode"></intro-view>
  </section>

  <section id="skill">
    <h2>Skills</h2>
    <skill-view :isDarkmode="isDarkmode"></skill-view>
  </section>

  <section id="project">
    <h2>Projects</h2>
    <project-view :isDarkmode="isDarkmode"></project-view>
  </section>

  <section id="posts">
    <h2>Posts</h2>
    <posts-view :isDarkmode="isDarkmode"></posts-view>
  </section>

  <section id="contact">
    <contact-view :isDarkmode="isDarkmode"></contact-view>
  </section>

  <footer-view></footer-view>

  <global-header-bar v-on:change-mode="toggleDarkmode()" />
  <global-top-button :isDarkmode="isDarkmode" active="#skill" />
</main>
</template>

<script>
import Intro from './components/views/Intro.vue'
import Skill from './components/views/Skill.vue'
import Project from './components/views/Project.vue'
import Posts from './components/views/Posts.vue'
import Contact from './components/views/Contact.vue'
import Footer from './components/views/Footer.vue'

import Header from './components/Header.vue'
import TopButton from './components/TopButton.vue'

export default {
  name: 'App',
  components: {
    'IntroView': Intro,
    'SkillView': Skill,
    'ProjectView': Project,
    'PostsView': Posts,
    'ContactView': Contact,
    'FooterView': Footer,
    'GlobalHeaderBar': Header,
    'GlobalTopButton': TopButton,
  },
  data: () => {
    return {
      isDarkmode: false,
    }
  },
  methods: {
    toggleDarkmode () {
      this.isDarkmode = !this.isDarkmode;
    }
  }
}
</script>

<style scoped>
@keyframes FadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

main {
  width: 100%;
  height: 100%;

  position: absolute;
  top: 0;
  left: 0;

  transition: background-color .3s ease-in-out;
  scroll-behavior: smooth;
}

section {
  width: 100%;
  height: fit-content;
  padding: 100px 0;

  position: relative;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#intro {
  height: 100%;
  padding: 0;

  justify-content: center;
  align-items: center;
}

#skill {
  background-color: ghostwhite;
}

#contact {
  padding-bottom: 200px;
}

h2 {
  font-size: 40px;
  margin: 30px;
  color: dodgerblue;
}

main.dark > section {
  background-color: #0D0D0D;
}

main.dark #skill {
  background-color: #262626;
}

@media screen and (max-width: 700px) {
  h2 {
    font-size: 30px;
    margin: 10px;
  }
}
</style>
