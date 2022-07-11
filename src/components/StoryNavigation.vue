<template>
  <div class="navigation-wrapper">
    <div v-for="(button, index) in $attrs.buttons" :key="index" class="navigation-item" v-on:click="updateFrame(button.linkindex)">
      {{ button.text }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'StoryNavigation',
  methods: {
    updateFrame: function(newFrameIndex){
      this.$parent.$parent.getNewFrameIndex(newFrameIndex)
    }
  }
}
</script>

<style scoped>

</style>
