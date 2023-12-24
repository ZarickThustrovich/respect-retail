<script lang='ts' setup>
// import Comment from './components/tree/comment.vue'
import RecursiveMenu from './components/tree/RecursiveMenu.vue'
</script> 
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'About',
    data() {
        return {
          menu: [
            { label: "Пункт 1", submenu: [{ label: "Подпункт 1-1" }, { label: "Подпункт 1-2" }] },
            { label: "Пункт 2", submenu: [{ label: "Подпункт 2-1" }, { label: "Подпункт 2-2" }] },
            { label: "Пункт 3" },
          ],
        };
    },
    methods: {
      handleShowSubmenu(submenu:any) {
        // Здесь можно обработать отображение следующего уровня меню
        console.log("Отображено подменю:", submenu);
      },
    },
    components: {
      RecursiveMenu,
  },
})
</script>

<template>
  <div class='content'>
    
  </div>
  <div class="menu">
    <recursive-menu :menu-items="menu" @show-submenu="handleShowSubmenu" />
  </div>
</template>
<style>

.comments ul {
  padding-left: 16px;
  margin: 6px 0;
}
.comments {
  color: black;
}
.comments > ul > li {
  color: black;
}
</style>