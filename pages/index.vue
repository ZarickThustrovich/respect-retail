<script setup lang="ts">
import Accordion from './components/accordion/accordion.vue'
</script>
<script lang="ts">
  import { defineComponent } from "vue"
  export default defineComponent({
    name: "Main",
    data() {
      return {
        layers: 4,
        accordionOptions: [
          {
            panel: {
              text: 'Панель №1',
              direction: 'default',
            },
            content: {
              text: 'Контент №1 \n dasdaspoaskdaspokdoaspk Контент №1 \n asdksapodksaodksapodsaop \n dasdaspoaskdaspokdoaspk',
            },
          },
          {
            panel: {
              text: 'Панель №2',
              direction: 'default',
            },
            content: {
              text: 'Контент №2',
            },
          },
          {
            panel: {
              text: 'Панель №3',
              direction: 'default',
            },
            content: {
              text: 'Контент №3',
            },
          }
        ]
      }
    },
  })
</script>
<template>
  <div class='backgrounded-block content'>
    <div>
      <p class='page-title'>MAIN</p>
      <Accordion :options='accordionOptions' />
    </div>
  </div> 
</template>
<style>
  .backgrounded-block{
    background-image: url('../assets/index-background.png');
    background-repeat: no-repeat;
    background-size: cover;
    height: 80vh;
    width: 100%;
    padding-top: 6vh;
    top: 0;
  }
</style>
