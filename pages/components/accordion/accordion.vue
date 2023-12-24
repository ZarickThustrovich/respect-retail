<script lang="ts" setup>
  import AccordionElement from './accordionElement.vue'
  const { options } = defineProps<Accordion>()
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
  interface Accordion {
    options: Array<AccordionObject>,
  }

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Accordion',
  data() {
    return {
      accordionHeight: this.options.length * 4 * 2 + 'vh'
    }
  },
})
</script>

<template>
  <div class='accordion'>
    <AccordionElement v-for='(option, index) in options' :panel='option.panel' :content='option.content' :key='index' />
  </div>
</template>
<style>
.accordion {
  width: '100%';
  min-height: v-bind(accordionHeight);
}
</style>