<template>
  <div id="app">
    <div class="frame-wrapper" :class="`${loading ? 'loading' : ''}`">
    <transition name="fade-scale">
      <LoadingFrame v-if="loading" />
      <StoryFrame v-else :pageNumber="currentFrame+1" :title="storyBoard.title" :body="storyBoard.body" :img="storyBoard.img" :buttons="storyBoard.buttons" />
    </transition>
    </div>
  </div>
</template>

<script>
import StoryFrame from './components/StoryFrame.vue'
import LoadingFrame from './components/LoadingFrame.vue'

export default {
  name: 'App',
  el: '#app',
  components: {
    StoryFrame,
    LoadingFrame
  },
  data() {
    return {
			loading:true,
      storyBoard: {},
      currentFrame: 0,
		}
  },
  beforeMount: function() {
    },
  mounted: function(){
      this.loading = false,
      this.root = document.documentElement;
      this.updateFrame(this.currentFrame);
  },
  methods: {
    updateFrame: async function(frameIndex) {
      this.loading = true;
      try {
        const res = await fetch('http://localhost:3000/frames')
          .then(response => response.json());
        this.storyBoard = res[frameIndex];
        this.updateCss();
        this.loading = false;
      } catch (error) {
        console.log(error);
      }
    },
    updateCss: function(){
      this.root.style.setProperty("--bg", this.storyBoard.colors.bg);
      this.root.style.setProperty("--text", this.storyBoard.colors.text);
    },
    getNewFrameIndex: function(newFrameIndex){
      this.currentFrame = newFrameIndex;
      this.updateFrame(newFrameIndex);
    }
  }
}
</script>