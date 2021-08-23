<template>
<div id="container" :class="{dark: isDarkmode}">
  <div class="project-item" v-for="(project, index) in projects" :key="project.id">
    <project-item
      :isDarkmode="isDarkmode"
      :data="project"
      :rightAlign="index%2 != 0 ? true : false"
    />
  </div>

  <light-button href="https://github.com/yejun614" text="Discovery more projects in Github" :newTab="true" />
</div>
</template>

<script>
import ProjectItem from './ProjectItem.vue'
import LightButton from '../button/LightButton.vue'
import SkillData from '../../data/projects.json'

export default {
  props: ['isDarkmode'],
  components: {
    ProjectItem,
    LightButton,
  },
  data: () => {
    return {
      projects: SkillData,
    }
  }
}
</script>

<style scoped>
#container {
  width: 800px;
  margin: 70px;

  display: flex;
  flex-direction: column;
}

@media screen and (max-width: 700px) {
  #container {
    width: 90%;
    align-items: center;
  }

  .project-item {
    width: 100%;
  }
}
</style>
