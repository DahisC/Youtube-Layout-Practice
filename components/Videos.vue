<template>
  <div class="video__wrapper">
    <template v-for="(video, i) in videoList">
      <div
        v-if="i < pagination.limit + pagination.offset"
        class="video"
        :key="i"
      >
        <div class="video__header">
          <a
            class="video__preview-image"
            href=""
            :style="{ backgroundImage: `url(${video.media.previewImage})` }"
          >
            <!-- <img :src="video.media.previewImage" alt="" /> -->
          </a>
          <span class="video__duration">1:30</span>
        </div>
        <div class="video__body">
          <a class="video__author-avatar" href="#">
            <img :src="video.author.avatar" alt="" />
          </a>
          <div class="video__info">
            <h3 class="video__title">{{ video.title }}</h3>
            <div class="video__detail">
              <span class="video__author-name">{{ video.author.name }}</span>
              •
              <span class="video__views">{{ video.views | views }} views</span>
              •
              <span class="video__created-at"
                >{{ video.createdAt | createdAt }} 前</span
              >
            </div>
          </div>
          <button class="video__menu custom-button">
            <img src="/imgs/more.svg" alt="" />
          </button>
        </div>
      </div>
    </template>
    <!-- Pagination -->
    <div v-if="isPaginationNeeded" class="video__more">
      <!-- {{ isPaginationNeeded }} -->
      <button class="custom-button" @click="loadVideos">
        <img src="/imgs/load.svg" alt="load button" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      decive: null,
      videoList: [
        {
          title:
            '男子受夠鄰居經常大聲放音樂，偷連鄰居的藍芽喇叭播放自創曲，嗆爆鄰居 (中文字幕)',
          views: '100',
          createdAt: '2021-08-17T00:10:37.444Z',
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/u08q3q2qkMA/hqdefault.webp',
            duration: '31',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLSqSm1JsLlsmODvhfJkGIVBpVQaTVVonr-YAgeo=s100-c-k-c0x00ffffff-no-rj',
            name: 'B.C&Lowy',
          },
        },
        {
          title:
            '喜歡日本女高中生？一定要懂她們的語言！一起來考「JK語」檢定一口氣學完日文流行用語！【RYUUUTV學日文2018】#005',
          views: '289542',
          createdAt: '2021-06-17T00:10:37.444Z',
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/R8dlD-cO0aI/sddefault.webp',
            duration: '852',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLRIKx1t3vFRyqJ9vrGOfXFTCiHITngZSPwha6u_wQ=s68-c-k-c0x00ffffff-no-rj',
            name: 'Ryuuu TV / 學日文看日本',
          },
        },
        {
          title: '日語聽力技巧 - 聽到不懂的字又何妨 ! ?',
          views: '75421',
          createdAt: '2021-08-14T00:10:37.444Z',
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/CvnNrKu54rw/sddefault.webp',
            duration: '341',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLRknpUvfOHKluk5Tmg3jHmucSLK63V5y3GvrhCrbQ=s68-c-k-c0x00ffffff-no-rj',
            name: 'AKIRA放送/日語教學網',
          },
        },
        {
          title:
            '【國語】進擊的巨人S1 第01話【給二千年後的你】 |Muse木棉花 動畫 線上看',
          views: '8216231',
          createdAt: '2020-08-17T00:10:37.444Z',
          media: {
            previewImage: 'https://i.ytimg.com/vi/PQia56ueJvk/sddefault.jpg',
            duration: '1550',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLTTHp_J9at0FzmyJ2n9ODG37zTxsHfiQg3MgVrjYA=s68-c-k-c0x00ffffff-no-rj',
            name: 'Muse木棉花-TW',
          },
        },
        {
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/U9xVCEabM4k/sddefault.webp',
            duration: '4255',
          },
          title: '2015 LMS 夏季總決賽 Day3 HKE vs ahq Game 1',
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLSP9LxrNfAZIz0L_iE1OWC8XrSnXD2atZbLbXgQ6Q=s68-c-k-c0x00ffffff-no-rj',
            name: 'Garena Esports',
          },
          views: '208135',
          createdAt: '2018-08-17T00:10:37.444Z',
        },
        {
          title: '【國動】達瑞斯叔叔 各種打胎 -經典系列by蔡播',
          views: '901471',
          createdAt: '2021-08-17T00:10:37.444Z',
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/ZJJC7ia51y8/hqdefault.webp',
            duration: '116',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLTB80nWCxolbLExofvvuHmwnYzCIcCEOrVUbAOx9A=s68-c-k-c0x00ffffff-no-rj',
            name: '鼻地大師國動-張葦航',
          },
        },
        {
          title: '[1hour] DJ Okawari - Flower Dance',
          views: '224714',
          createdAt: '2021-03-17T00:10:37.444Z',
          media: {
            previewImage:
              'https://i.ytimg.com/vi_webp/FiPfBqP2nsM/sddefault.webp',
            duration: '3051',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLSGvehubRhZed2RDqEvIMNaLn56dCIQCtvlgkPH=s68-c-k-c0x00ffffff-no-rj',
            name: '1hour player',
          },
        },
        {
          title:
            '【從零開始養】寵物狐狸!狐狸有狐臭?把食盆當小便斗?跟狗誰好養?【許伯簡芝】fox',
          views: '2810561',
          createdAt: '2021-01-17T00:10:37.444Z',
          media: {
            previewImage: 'https://i.ytimg.com/vi/udEdGUmKW4U/sddefault.jpg',
            duration: '786',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLRB6DnjEBEQKdJ3V3gJK5YgM6W6jROP52vrOrEi8w=s68-c-k-c0x00ffffff-no-rj',
            name: '許伯&簡芝—倉鼠人',
          },
        },
        {
          title: '《住宅改造王》 百年和服店變身豪華住宅！(上)【HD】',
          views: '241212',
          createdAt: '2021-08-16T00:10:37.444Z',
          media: {
            previewImage: 'https://i.ytimg.com/vi/FnwAWzouyNY/sddefault.jpg',
            duration: '2341',
          },
          author: {
            avatar:
              'https://yt3.ggpht.com/ytc/AKedOLT2ak8-_Z2vRl5oF6CGcESZ3wwNJAU_47lmYKsJCg=s68-c-k-c0x00ffffff-no-rj',
            name: '緯來日本台',
          },
        },
      ],
      pagination: {
        rowCount: null,
        limit: null,
        offset: null,
      },
    }
  },
  mounted() {
    this.detectDevice()
  },
  methods: {
    detectDevice() {
      const w = window.innerWidth

      const setPagination = (limit, rowCount) => {
        this.pagination.limit = limit
        this.pagination.rowCount = rowCount
      }

      if (w >= 1440) return setPagination(8, 4)
      if (w >= 1024) return setPagination(6, 3)
      if (w >= 768) return setPagination(4, 4)
      if (w >= 320) return setPagination(4, 2)
    },
    loadVideos() {
      this.pagination.offset += this.pagination.rowCount
    },
  },
  filters: {
    views(count) {
      if (count > 1000000) return (count / 1000000).toFixed(1) + 'M'
      if (count > 1000) return Math.floor(count / 1000) + 'K'
      return count
    },
    createdAt(date) {
      const hour = 60 * 1000,
        day = 24 * 60 * 60 * 1000,
        week = day * 7,
        month = day * 30,
        year = month * 12,
        dateInMidleseconds = Date.parse(date),
        now = Date.parse(new Date()),
        difference = now - dateInMidleseconds

      if (difference > year) return Math.floor(difference / year) + ' 年'
      if (difference > month) return Math.floor(difference / month) + ' 個月'
      if (difference > week) return Math.floor(difference / week) + ' 週'
      if (difference > day) return Math.floor(difference / day) + ' 天'
      return Math.floor(difference / hour) + ' 小時'
    },
  },
  computed: {
    isPaginationNeeded() {
      return (
        this.pagination.limit + this.pagination.offset < this.videoList.length
      )
    },
  },
}
</script>

<style scoped lang="scss">
.video__wrapper {
  display: flex;
  flex-wrap: wrap;
}
.video {
  flex-basis: 100%;
  &:not(:last-child) {
    margin-bottom: 15px;
  }
  .video__header {
    position: relative;
    .video__preview-image {
      display: block;
      width: 100%;
      padding-bottom: 75%; // forcing 4:3 aspect ratio
      background-size: cover;
      background-repeat: no-repeat;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .video__duration {
      position: absolute;
      bottom: 0;
      right: 0;
      margin: 5px 7px;
      padding: 1px 3px;
      border-radius: 3px;
      background-color: #000;
      color: #fff;
    }
  }
  .video__body {
    display: flex;
    flex-direction: row;
    padding: 10px;
    .video__author-avatar {
      flex-shrink: 0;
      width: 40px;
      height: 40px;
      display: block;
      border-radius: 50%;
      overflow: hidden;
      margin-right: 10px;
    }
    .video__title {
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
      margin: 0 0 5px;
      font-size: 1.4rem;
    }
    .video__detail {
      opacity: 0.6;
      font-size: 1.2rem;
    }
    .video__menu {
      margin-left: auto;
      margin-bottom: auto;
    }
  }
}

/* RWD */
@media (min-width: 768px) {
  .video__wrapper {
    padding: 7.5px;
  }
  .video {
    flex-basis: calc(50% - 15px);
    margin: 7.5px;
    .video__body {
      padding: 10px 0px;
    }
  }
}

@media (min-width: 1024px) {
  .video {
    flex-basis: calc(33.3% - 15px);
  }
}
@media (min-width: 1440px) {
  .video {
    flex-basis: calc(25% - 15px);
  }
}

.video__more {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 15px;
}
</style>
