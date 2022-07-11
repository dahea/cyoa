<template>
  <div class="frame story-frame">
    <div class="page-number">{{pageNumber}}</div>
    <h1>{{ title }}</h1>
    <div class="copy-wrapper" :class="`${img ? 'support-img' : ''}`">
      <div class="copy" v-html="body"></div>
      <img v-if="img" :src="require(`@/assets/${img}`)" />
    </div>
    <StoryNavigation v-if="buttons" :buttons="buttons"/>
    
  </div>
</template>

<script>

import StoryNavigation from './StoryNavigation.vue'

export default {
    name: "StoryFrame",
    components: {StoryNavigation},
    props: {
        pageNumber: Number,
        title: String,
        body: String,
        img: String,
        buttons: Array,
    },
}
</script>