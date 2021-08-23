<template>
<div id="container" :class="{dark: isDarkmode}">
  <div class="item" v-for="item in skillset" :key="item.id">
    <img :src="item.imgSrc" alt="Skill icon" />
    <h3>{{ item.title }}</h3>
    <span>{{ item.contents }}</span>
  </div>
</div>
</template>

<script>
export default {
  name: 'Skill',
  props: ['isDarkmode'],
  data: () => {
    return {
      skillset: [
        {
          "id": 1,
          "imgSrc": require("../../assets/skill/web.png"),
          "title": "Frontend",
          "contents": "다양한 유형의 웹사이트를 제작, 배포합니다. 반응형, 다크모드, PWA 등 현대적이고 실용적인 기능을 추구합니다."
        },
        {
          "id": 2,
          "imgSrc": require("../../assets/skill/cloud.png"),
          "title": "Backend",
          "contents": "Restful API, Headless CMS, Serverless, Docker를 공부하고 있습니다. 성능을 중요하게 생각합니다."
        },
        {
          "id": 3,
          "imgSrc": require("../../assets/skill/game.png"),
          "title": "Game Client",
          "contents": "플랫포머 부터 Full 3D 게임 까지 제작합니다. JavaScript, Godot, Unity 등을 사용합니다."
        }
      ]
    }
  }
}
</script>

<style scoped>
#container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
}

.item {
  width: 230px;
  padding: 30px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  position: relative;
}

.item::after {
  content: '';
  width: 1px;
  height: 50px;
  border-right: 1px solid #0074D9;

  position: absolute;
  right: 0;
}

.item:last-child:after {
  content: '';
  border: none;
}

.item img {
  width: 120px;
  height: 120px;
  margin: 30px 0;

  transition: transform .3s ease-in-out;
}

.item img:hover {
  transform: translate(0, -10px);
}

.item h3 {
  font-size: 20px;
  font-weight: bold;
}

#container.dark .item h3 {
  color: #ccc;
}

.item span {
  color: #595959;
  text-align: center;
  padding: 15px 0;
}

#container.dark .item span {
  color: #aaa;
}

@media screen and (max-width: 700px) {
  #container {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr;
  }

  .item::after {
    content: '';
    width: 50px;
    height: 1px;
    border-right: none;
    border-bottom: 1px solid #0074D9;

    position: absolute;
    right: auto;
    bottom: 0;
  }

  .item:last-child:after {
    content: '';
    border: none;
  }
}
</style>
