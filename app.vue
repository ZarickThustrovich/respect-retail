<script text="ts" setup>
  import Header from './header.vue';
  import Footer from './footer.vue'
  const navigation = [
    { label: 'Главная', to: '/' },
    { label: 'О нас', to: '/about' },
  ]
</script>

<template>
  <div>
    <Header :navigation='navigation' />
    <div>
      <NuxtPage />
    </div>
    <Footer />
  </div>
</template>
<style>
  a {
    text-decoration: none;
    color: unset;
  }
  .page-title {
    font-size: 2.5em;
    font-weight: bold;
  }
  body {
    margin: 0;
  }
  .content {
    padding-top: 6vh;
  }
  .content > div{
    width: 90%;
    margin: 0 auto;
    
  }
</style>
