<script lang="ts" setup>
  const { panel, content } = defineProps<AccordionObject>()
</script>

<script lang="ts">
  interface AccordionPanel {
    text: string,
    direction: string,
  }
  interface AccordionContent {
    text: string,
  }
  interface AccordionObject {
    panel: AccordionPanel,
    content: AccordionContent,
  }

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AccordionElement',
  data() {
    return {
      contentCollapsed: false
    }
  },
  methods: {
    toggleContentState () {
      this.contentCollapsed = !this.contentCollapsed
    }
  },
  computed: {
    panelContentState(){
      return this.contentCollapsed ? 'collapsed' : 'collapsible'
    }
  },
})
</script>

<template>
  <div class='panel'>
    <button 
    class='accordion-button panel-text'
    @click='toggleContentState()'>{{ panel.text }}</button>
    <div
    class='panel-content'
    :class="panelContentState">{{ content.text }}</div>
  </div>
</template>
<style>
.panel{
  border: 1px solid rgb(206, 206, 206);
  background-color: rgb(206, 206, 206);
}
.panel-text{
  font-size: 1em;
  font-weight: bold;
}
.panel-content{
  height: 0;
  padding-left: 0.5em;
  transition: min-height 0.3s ease-out;
  &.collapsible {
    min-height: 0;
    text-indent: 100%;
    white-space: nowrap;
    overflow: hidden;
  }
  &.collapsed {
    min-height: 4vh;
  }
}
.accordion-button{
  height: 5vh;
  width: 100%;
}
</style>