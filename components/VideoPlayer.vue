<template>
  <div id="video-player-component">
    <h1>I'm counting: {{count}}</h1>
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
import CustomButton from '@/video-components/customButton'

videojs.registerComponent('CustomButton', CustomButton)

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
  data:()=>{
    return {
      count : 0
    }
  },
  mounted(){
    const videoPlayer = this.$refs["videoPlayer"]
    const player = videojs(videoPlayer, videoConfig, ()=>{
      player.controlBar.addChild("CustomButton", {
        onClick:()=>{
          this.count++
        }
      })
    })
  }
})
</script>
<style>
.vjs-custom{
  cursor: pointer;
  font-size: 1.8em!important;
  color:white;
}
</style>
