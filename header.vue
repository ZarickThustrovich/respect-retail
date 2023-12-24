<script setup lang="ts">
  import type { StyleValue } from 'vue';
  import { defineComponent } from 'vue'
  import { useRoute } from 'vue-router'
  const { navigation } = defineProps<navigation>()
</script>
<script lang="ts">

  interface navigationObject {
    to: string,
    label: string,
  }
  
  interface navigation {
    navigation: Array<navigationObject>,
  }
  
export default defineComponent({
  name: 'Header',
  data() {
    return {
    }
  },
  computed: {
    headerStyle() {
      const location = useRoute();
      const headerStyle:Partial<StyleValue> = { 
        backgroundColor: `rgb(255, 255, 255, ${location.path === '/' ? '0' : '1'})`,
        color: location.path === '/' ? "white" : "#720f72",
      }
      return headerStyle
    },
    listItemStyle() {
      const location = useRoute();
      const listItemStyle:Partial<StyleValue> = {
        borderColor: location.path === '/' ? "white" : "#720f72",
      }
    }
  },
})

</script>
<template>
  <div
  class='header'
  :style='headerStyle'
  >
    <NuxtLink
      class='link-style'
      :style='listItemStyle'
      v-for='link in navigation'
      :key='link.to'
      :to='link.to'>
        {{ link.label }}
    </NuxtLink>
  </div>
</template>
<style>
  .link-style {
    font-size: 1.5em;
    font-weight: 200;
    border-bottom: 1px solid;
    text-decoration: none;
    align-self: center;
  }
  .router-link-active {
    border-bottom: 2px solid;
    font-weight: 400;
  }
  .header {
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    width: 100vw;
    gap: 2rem;
    z-index: 2;
    position: fixed;
    top: 0;
    border-bottom: 1px solid #E0E0E0;
    height: 5vh;
    padding: 1vh 10vh 1vh 10vh;
  }
</style>