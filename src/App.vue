<template>
  <div id="app">
    <div class="frame-wrapper" :class="`${loading ? 'loading' : ''}`">
    <LoadingFrame v-if="loading" />
    <StoryFrame v-else :pageNumber="currentFrame+1" :title="storyBoard[currentFrame].title" :body="storyBoard[currentFrame].body" :img="storyBoard[currentFrame].img" :buttons="storyBoard[currentFrame].buttons"/>
    </div>
  </div>
</template>

<script>
import StoryFrame from './components/StoryFrame.vue'
import LoadingFrame from './components/LoadingFrame.vue'
import storyData from "./assets/data/story.json";

export default {
  name: 'App',
  components: {
    StoryFrame,
    LoadingFrame
  },
  data() {
    return {
			loading:true,
      storyBoard: [],
      currentFrame: 0,
		}
  },
  beforeMount: function() {
      this.storyBoard = storyData.frames
  },
  mounted: function(){
      this.loading = false,
      this.root = document.documentElement;
      this.updateCss();
  },
  methods: {
    updateCss: function(){
      this.root.style.setProperty("--bg", this.storyBoard[this.currentFrame].colors.bg);
      this.root.style.setProperty("--text", this.storyBoard[this.currentFrame].colors.text);
    },
    updateFrame: function(newFrameIndex){
      this.currentFrame = newFrameIndex;
      this.updateCss()
    }
  }
  
}
</script>