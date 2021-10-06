<template>
  <div>
    <div id="mountains-list">
      <div id="mountains-item" v-for="mont in mountains" :key="mont.id">
        <div><img :src="mont.image" alt="" srcset="" /></div>
        <div class="description">{{ mont.description }}</div>
        <div class="">{{ mont.title }}</div>
        <div class="">{{ mont.height }}</div> 
        <div class="">{{ mont.continent }}</div>
        <div class="">{{ mont.updatedAt }}</div>
        <nuxt-link :to="`/mountains/${mont.slug}`">detalhes</nuxt-link>
        <!-- dir: '/mountains',
        path: '/mountains/aconcagua',
        slug: 'aconcagua', :
        '2020-12-11T15:40:35.000Z' -->
        <div></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios }) {
    const mountains = await $axios.$get("https://api.nuxtjs.dev/mountains");
    console.log(mountains);
    return { mountains };
  },
};
</script>
<style scoped>
#mountains-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 20px;
}
img {
  height: 300px;
  width: 100%;
}
#mountains-item {
  max-width: calc((100% / 2) - 30px);
  box-shadow: 0 0 1em #555;
  padding: 10px;
}
div {
  font-size: 1rem;
  font-family: monospace;
  color: #333;
}
</style>
