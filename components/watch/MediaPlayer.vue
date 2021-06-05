<template>
  <div class="player-container mx-0 pb-2">
    <div class="flex flex-wrap">
      <div class="w-full xl:w-2/3 xl:px-3 xl:mb-0">
        <video ref="player" class="video-js vjs-fluid vjs-16-9 vjs-big-play-centered">
          <p class="vjs-no-js">
            Sorry, Swish can't be used on your browser. Try upgrading to a more
            modern browser.
          </p>
        </video>
      </div>
      <div class="w-full xl:w-1/3 xl:px-3">
        <div class="bg-teal-100 text-teal-900 p-6 pt-8 shadow-md" role="alert">
          <div class="flex">
            <div>
              <h1 class="text-4xl mb-6">
                <span class="font-medium">Title film</span> (2021)
              </h1>
              <p class="subtitle-list-intro text-2xl text-gray-300">
                Dưới đây là các phụ đề của phim này được hệ thống lấy tự động từ subscene.com. Nếu chọn được một phụ đề vừa ý (khớp thời gian &amp; dịch chuẩn), hãy Like phụ đề đó để lần sau xem lại phim, hệ thống sẽ tự động sử dụng phụ đề đó cho bạn!
              </p>
              <p class="text-2xl text-gray-300 mt-4">
                Bạn cũng có thể upload file phụ đề của riêng bạn =&gt; <a href="#">Click vào đây!</a>
              </p>
              <p class="text-2xl text-gray-300">
                <a href="https://subscene.com/subtitles/cruella" target="_blank">Tìm phụ đề cho phim này trên Subscene</a>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
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
  .player-container {
    width: 100%;
    height: 100%;
    .video-js {
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
