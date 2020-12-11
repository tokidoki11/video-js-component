<template>
  <div class="container">
    <VideoPlayer/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import VideoPlayer from '@/components/VideoPlayer.vue'

export default Vue.extend({
  components:{
    VideoPlayer
  }
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
