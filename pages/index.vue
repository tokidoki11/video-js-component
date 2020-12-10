<template>
  <div class="container">
   <video
    ref="videoPlayer"
    class="video-js vjs-show-big-play-button-on-pause vjs-big-play-centered"
    muted
  />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import videojs, { VideoJsPlayerOptions } from 'video.js'

const videoConfig = {
  autoplay: true,
  controls: true,
  html5: {
    vhs: {
      allowSeeksWithinUnsafeLiveWindow: true,
      enableLowInitialPlaylist: true,
      overrideNative: false,
      smoothQualityChange: true,
      withCredentials: false
    }
  },
  inactivityTimeout: 0,
  sources: [{
    src: "https://live.unified-streaming.com/scte35/scte35.isml/.m3u8",
    type: 'application/x-mpegURL'
  }],
  liveui: true,
  muted: true,
  preload: 'auto',
  width:720
} as VideoJsPlayerOptions

export default Vue.extend({
  mounted(){
    const videoPlayer = this.$refs["videoPlayer"]
    videojs(videoPlayer, videoConfig)
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
