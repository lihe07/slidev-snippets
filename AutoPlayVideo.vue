<script setup>
  import {watchEffect,ref} from "vue"
  const props = defineProps(["src"]);
  
  const ele = ref(null)
  function onEnter() {
    if (!ele.value) return
    console.log("ref", ele.value)
    ele.value.currentTime = 0
    ele.value.play()
  }

  watchEffect(() => {
    if ($page.value === $slidev.nav.currentPage) onEnter()
  });
  
</script>

<template>
  <video :src="props.src" ref="ele"  />
</template>
