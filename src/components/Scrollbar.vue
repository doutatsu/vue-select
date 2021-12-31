<template>
  <div ref="element" tabindex="0">
    <slot></slot>
  </div>
</template>

<script setup>
import 'overlayscrollbars/css/OverlayScrollbars.css'
import OverlayScrollbars from 'overlayscrollbars'
import { onMounted, onUnmounted, ref } from 'vue'

let instance
const element = ref(null)

onMounted(() => {
  instance = OverlayScrollbars(element.value, {
    scrollbars: { autoHide: 'move' },
  })
})

onUnmounted(() => {
  instance.destroy()
})
</script>

<style lang="scss">
.os-viewport {
  overscroll-behavior-block: contain;
}
</style>
