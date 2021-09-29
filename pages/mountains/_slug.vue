<template>
  <div>
    <h1>Continent: {{}}</h1>
    <h2>Mountain: {{}}</h2>
    <p>Path: {{ $route.path }}</p>
    <NuxtLink to="/">voltar inicio</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios }) {
    const mountains = await $axios.$get("https://api.nuxtjs.dev/mountains");
    console.log(mountains);
  },
};
</script>
