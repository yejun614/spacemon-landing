<template>
<div id="item" :class="{dark: isDarkmode, right : rightAlign}">
  <div class="thumbnail" ref="thumbnail" v-if="!rightAlign"></div>

  <div class="content">
    <h3>{{ data.title }}</h3>
    <span>{{ data.text }}</span>
    <slim-button :href="data.link" :text="data.title" :newTab="true" />
  </div>

  <div class="thumbnail" ref="thumbnail" v-if="rightAlign"></div>
</div>
</template>

<script>
import SlimButton from '../button/SlimButton.vue'

export default {
  props: ['isDarkmode', 'data', 'rightAlign'],
  components: {
    SlimButton,
  },
  mounted () {
    const thumbnail = this.$refs.thumbnail;
    thumbnail.style = `background-image: url('${this.data.imgSrc}');`;
  }
}
</script>

<style scoped>
#item {
  display: flex;
  position: relative;
}

.content, .thumbnail {
  width: 400px;
  height: 400px;
}

.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#item.right .content {
  align-items: flex-end;
}

h3 {
  font-size: 25px;
  margin: 10px 25px;
}

#item.dark h3 {
  color: white;
}

span {
  color: #777;
  font-size: 14px;
  margin: 10px 25px;
}

#item.right span {
  text-align: right;
}

.thumbnail {
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;

  border-radius: 10px;
}

@media screen and (max-width: 700px) {
  #item {
    width: 100%;
    
    flex-direction: column;
    box-shadow: 1px 1px 2px #777;

    margin: 20px 0;
  }

  #item.dark {
    box-shadow: none;
  }

  .content, .thumbnail {
    width: 100%;
  }

  .content {
    height: fit-content;
    background-color: white;
  }

  #item.dark .content {
    background-color: #262626;
  }

  #item.right .content {
    position: relative;
    top: 200px;
    margin-bottom: 200px;
    align-items: flex-start;
  }

  #item.right .content span {
    text-align: left;
  }

  #item.right .thumbnail {
    position: absolute;
    top: 0;
  }

  .thumbnail {
    height: 200px;
    border-radius: 0;
  }

  .thumbnail * {
    display: none;
  }
}
</style>