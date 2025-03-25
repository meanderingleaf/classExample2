<script setup lang="jsx">
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Pageune from './components/PageUn.vue'
import Pagedeux from './components/PageDeux.vue'
import Button from 'primevue/button'
import Card from 'primevue/card'
import Panel from 'primevue/panel';


var currentPage = ref("Une")

const pages = {
  "Une": Pageune,
  "Deux": Pagedeux
}

const imageUrls = [
  '@/assets/image1.png',
  '@/assets/image2.png',
  '@/assets/image3.png'
]

const changePage = (page) => {
  currentPage.value = page
}
</script>

<template>
  <div>
    <Panel header="Hello World">
        <Card v-for="url in imageUrls" :key="url">
        <template #title>Image</template>
        <template #content>
            <img :src="url" />
        </template>
      </Card>
    </Panel>

    <component :is="pages[currentPage]" />
    <Button @click="changePage('Une')" label="Page Une" />
    <button @click="changePage('Deux')">Page Deux</button>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
