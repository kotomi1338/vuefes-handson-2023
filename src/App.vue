<script setup>
import { ref } from 'vue'
import Card from './components/Card.vue'

const items = ref([
  {
    id: 1,
    name: 'アボカドーパラダイスディップ',
    description:
      'さあ、口福の緑色楽園へようこそ！「アボカドーパラダイスディップ」は、新鮮な野菜の宝石をクリーミーなアボカドと絶妙にミックス。これを香ばしいバゲットにディップすれば、至福の一時があなたを待っています。これぞ、アボカド愛好家の夢の具現化！',
    price: 480,
    image: '/images/item1.jpg',
    soldOut: false,
    selected: false
  },
  {
    id: 2,
    name: 'ノスタルジック・ドリームホットケーキ',
    description:
      '子供の頃、窓の外で遊ぶ夢を見ながら食べたかった、あの「ノスタルジック・ドリームホットケーキ」がここに。素朴ながらも心温まる味わいは、懐かしさと幸せを一緒にお届けします。あなたを夢とともに、甘美な時へ誘います。',
    price: 1180,
    image: '/images/item2.jpg',
    soldOut: false,
    selected: false
  },
  {
    id: 3,
    name: 'L.A.スパークル・ウォーター',
    description:
      'カリフォルニアの日差しをボトルに閉じ込めた「L.A.スパークル・ウォーター」。ノンカロリーでノンアルコール、でも味わいは100％スペクタクル！ロサンゼルスからあなたのもとへ、キラキラ輝く水の魔法をお届けします。',
    price: 320,
    image: '/images/item3.jpg',
    soldOut: false,
    selected: false
  },
  {
    id: 4,
    name: 'チーズ・ヘブンフライズ',
    description:
      'イタリア直送のチーズをふんだんに使い、あなたをチーズの楽園へといざなう「チーズ・ヘブンフライズ」。アツアツのフレンチフライに贅沢にかけられたチーズは、まさに地上の楽園。一度食べれば、あなたもチーズの虜に。',
    price: 670,
    image: '/images/item4.jpg',
    soldOut: false,
    selected: false
  }
])
</script>

<template>
  <header class="header">
    <img
      src="/images/logo.svg"
      alt="">
    <h1>Vue.js ハンズオン</h1>
  </header>
  <main class="main">
    <template
      v-for="item in items"
      :key="item.id">
      <div
        v-if="!item.soldOut"
        class="item"
        :class="{ 'selected-item': item.selected }"
        @click="item.selected = !item.selected">
        <Card
          :id="item.id"
          :image="item.image"
          :name="item.name"
          :price="item.price">
          <template #body>
            <p>{{ item.description }}</p>
          </template>
        </Card>
      </div>
    </template>
  </main>
</template>

<style>
body {
  font-family: sans-serif;
  margin: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  width: 90%;
  margin: 0 5%;
  color: #242424;
}

.header {
  display: flex;
  align-content: center;
  align-items: center;
  margin-top: 40px;
  margin-bottom: 40px;
}

.header > img {
  width: 100px;
  height: 100px;
  margin-right: 20px;
}

.header > h1 {
  font-size: 80px;
  font-weight: bold;
  line-height: 80px;
  margin-top: 0;
  margin-bottom: 0;
}

.main {
  display: grid;
  grid-template-columns: 3fr 3fr 3fr 3fr;
  column-gap: 24px;
  row-gap: 24px;
}

.item {
  padding: 10px;
  cursor: pointer;
}

.item:hover {
  transition: 0.2s transform ease-out;
  transform: scale(1.05);
}

.selected-item {
  background-color: #e3f2fd;
}
</style>