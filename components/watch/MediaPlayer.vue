<template>
  <div class="container">
    <video ref="player" class="video-js vjs-16-9 vjs-big-play-centered">
      <p class="vjs-no-js">
        Sorry, Swish can't be used on your browser. Try upgrading to a more
        modern browser.
      </p>
    </video>
  </div>
</template>

<script>
import videojs from 'video.js'
import 'video.js/dist/video-js.css'
export default {
  data () {
    return {
      player: null
    }
  },
  watch: {},
  mounted () {
    this.player = videojs(this.$refs.player, {
      controls: true,
      autoplay: false,
      sources: [
        {
          src: 'https://www3.downloadstreamwatch.xyz/movies7/Search.And.Destroy.2020.English.720p.mp4',
          type: 'video/mp4'
        }
      ]
    })
    this.player.on('play', this.handleStart)
    this.player.on('ended', this.handleEnd)
    this.player.on('pause', this.handlePause)
  },
  beforeDestroy () {
    if (this.player) {
      this.player.dispose()
    }
  },
  methods: {
    handleStart () {
      console.log('start')
    },
    handleEnd () {
      console.log('end')
    },
    handlePause () {
      console.log('pause')
    }
    // playVideo (seasonIndex = 0, videoIndex = 0) {
    //   this.player.src(
    //     'https://www3.downloadstreamwatch.xyz/movies7/Search.And.Destroy.2020.English.720p.mp4'
    //   )
    //   this.player.play()
    // }
  }
}
</script>

<style lang="scss" scoped>
  .container {
    width: 100%;
    height: 100%;
    position: relative;
    margin: 0 auto;
    padding: 10px 0;
    .video-js {
      height: 100% !important;
      width: 100%;
      .vjs-big-play-button {
        border: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        font-size: 5em;
        height: 2em;
        width: 2em;
        margin-top: -1em;
        margin-left: -1em;
        border-radius: 50%;
        line-height: 2em;
      }
    }
  }
</style>
