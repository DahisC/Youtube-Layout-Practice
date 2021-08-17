<template>
  <div class="tags__wrapper">
    <span class="tag --active">全部</span>
    <span v-for="tag in tags" :key="tag" class="tag">{{ tag }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tags: [
        '卡通',
        '直播中',
        '烹飪節目',
        '合輯',
        '棒球',
        '健身',
        '數學',
        '音樂',
        '手工藝',
        '觀光',
        'Minecraft',
        '動作冒險遊戲',
        '恐怖',
        '寵物',
        '最新上傳',
      ],
    }
  },
}
</script>

<style scoped lang="scss">
// * {
//   scrollbar-width: none; /* Firefox */
// }

.tags__wrapper {
  --light-gray: rgba(0, 0, 0, 0.1);
  height: 48px;
  padding: 5px 10px;
  display: flex;
  flex-direction: row;
  align-items: center;
  border-bottom: 1px solid var(--light-gray);
  overflow-x: auto;
  /* Hide scrollbar for Chrome, Firefox, Safari and Opera */
  scrollbar-width: none; /* Firefox */
  &::-webkit-scrollbar {
    display: none; /* Chrome */
    -ms-overflow-style: none; /* IE and Edge */
  }
  > .tag {
    font-size: 1.4rem;
    border-radius: 999px;
    background-color: var(--light-gray);
    padding: 5px 10px;
    border: 1px solid var(--light-gray);
    word-break: keep-all;
    &:not(:last-child) {
      margin-right: 10px;
    }
    &.--active {
      background-color: rgba(0, 0, 0, 0.6);
      color: white;
    }
  }
}
</style>
