<template>
<div id="container" :class="{dark: isDarkmode}">
  <ul id="posts">
    <li class="item" v-for="post in posts" :key="post.id">
      <h3>{{ post.title }}</h3>
      <span>{{ post.contents }}</span>
    </li>

    <span class="no-posts" v-if="postLength == 0">
      There are no posts.
    </span>
  </ul>

  <slim-button href="#" text="More Contents" v-if="postLength > 0" />
</div>
</template>

<script>
import SlimButton from '../button/SlimButton.vue'
import PostList from '../../data/postlist.json'

export default {
  props: ['isDarkmode'],
  components: {
    SlimButton,
  },
  data: () => {
    return {
      posts: PostList,
      postLength: PostList.length,
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
  justify-content: center;
  align-items: center;
}

#posts {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  margin: 20px 0;
}

.item {
  width: 100%;
  padding: 10px;
  border-radius: 10px;

  display: flex;
  flex-direction: column;

  list-style: none;
  cursor: pointer;
}

.item:nth-child(odd) {
  background-color: ghostwhite;
}

#container.dark .item:nth-child(odd) {
  background-color: #141414;
}

.item h3 {
  margin: 10px;
}

.item span {
  margin: 10px;
  color: #777;
}

.no-posts {
  color: #777;
  font-size: 20px;
  font-weight: bold;
  border-bottom: 3px solid #777;
}

#container.dark .item h3 {
  color: #ccc;
}

@media screen and (max-width: 700px) {
  #container {
    width: 100%;
  }

  .item {
    width: 90%;
  }
}
</style>