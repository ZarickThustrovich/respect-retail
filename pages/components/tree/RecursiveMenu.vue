<!-- RecursiveMenu.vue -->

<template>
  <div class="menu">
    <div v-for="(item, index) in menuItems" :key="index">
      <div class="menu-item" @click="handleItemClick(item, index)">
        {{ item.label }}
      </div>
      <recursive-menu v-if="item.submenu" :menu-items="item.submenu" />
    </div>
  </div>
</template>

<script>
export default {
  name: "RecursiveMenu",
  props: {
    menuItems: {
      type: Array,
      required: true,
    },
  },
  methods: {
    handleItemClick(item, index) {
      if (item.submenu) {
        // Изменяем структуру данных для учета открытых и закрытых подпунктов
        this.$set(this.menuItems, index, {
          ...item,
          isOpen: !item.isOpen,
        });
      } else {
        console.log("Выбран пункт меню:", item.label);
      }
    },
  },
};
</script>

<style>
.menu {
  display: flex;
  flex-direction: column;
}

.menu-item {
  cursor: pointer;
  padding: 8px;
  border-bottom: 1px solid #ccc;
}

.menu-item:hover {
  background-color: #f0f0f0;
}
</style>
